import pandas as pd
import matplotlib.pyplot as plt

# Load data
data = pd.read_csv('traffic_data.csv')

# Calculate congestion level
data['Congestion'] = data['Vehicles'] / data['Signal Time']

# Show data
print(data)

# Plot graph
plt.plot(data['Time'], data['Congestion'])
plt.title("Traffic Congestion")
plt.xlabel("Time")
plt.ylabel("Congestion Level")
plt.show()


def optimize_signal(vehicles):
    if vehicles > 180:
        return 90
    elif vehicles > 120:
        return 75
    else:
        return 60

data['Optimized Signal'] = data['Vehicles'].apply(optimize_signal)

print(data)




plt.plot(data['Time'], data['Signal Time'], label='Old')
plt.plot(data['Time'], data['Optimized Signal'], label='Optimized')
plt.legend()
plt.title("Signal Optimization Comparison")
plt.show()