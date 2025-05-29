```
gradients_to_nodes(gradients::Matrix; gamma=42577478, dwellTime=2e-6, FOV=[220,220,1],reconSize=[200,200,1])
```

Function to calculate the k-space nodes from an applied gradient train

# Arguments

  * `gradients::Matrix` - input gradients played out, acquired with constant dwell time. Size: (`2` x `N`) where N is the number of gradient samples
  * `gamma` - gyromagnetic ratio [Hz]
  * `dwellTime` - the dwell time of the trajectory [s]
  * `FOV` - spatial field of view in [mm] [`1` x `3`]
  * `reconSize` - reconstruction matrix size [`1` x `3`]

# Outputs

  * `nodes::Matrix` - k-space nodes corresponding to applied gradient train. Size: (`2` x `N`) where N is the number of gradient samples
