```
nodes_to_gradients(nodes::Matrix; gamma=42577478, dwellTime=2e-6, FOV=[220,220,1],reconSize=[200,200,1])
```

Function to calculate the gradient train used to acquire k-space data

# Arguments

  * `nodes::Matrix` - input k-space nodes traversed in order, acquired with constant dwell time. Size: (`2` x `N`) where N is the number of nodes
  * `gamma` - gyromagnetic ratio [Hz]
  * `dwellTime` - the dwell time of the trajectory [s]
  * `FOV` - spatial field of view in [mm] [`1` x `3`]
  * `reconSize` - reconstruction matrix size [`1` x `3`]

# Outputs

  * `gradients::Matrix` - gradients corresponding to k-space samples. Size: (`2` x `N`) where N is the number of k-space samples
