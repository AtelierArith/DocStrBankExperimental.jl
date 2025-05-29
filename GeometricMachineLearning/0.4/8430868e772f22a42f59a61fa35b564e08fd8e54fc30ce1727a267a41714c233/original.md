```
VolumePreservingFeedForward(dim)
```

Make an instance of a volume-preserving feedforward neural network for a specific system dimension.    

This architecture is a composition of [`VolumePreservingLowerLayer`](@ref) and [`VolumePreservingUpperLayer`](@ref). 

# Arguments

You can provide the constructor with the following additional arguments:

2. `n_blocks::Int = 1`: The number of blocks in the neural network (containing linear layers and nonlinear layers).
3. `n_linear::Int = 1`: The number of linear `VolumePreservingLowerLayer`s and `VolumePreservingUpperLayer`s in one block.
4. `activation = tanh`: The activation function for the nonlinear layers in a block.

The following is a keyword argument:

  * `init_upper::Bool = false`: Specifies if the first layer is lower or upper.
