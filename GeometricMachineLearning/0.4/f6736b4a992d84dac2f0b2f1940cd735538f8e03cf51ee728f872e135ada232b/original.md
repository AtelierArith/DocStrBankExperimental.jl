```
VolumePreservingTransformer(sys_dim, seq_length)
```

Make an instance of the volume-preserving transformer for a given system dimension and sequence length.

# Arguments

The following are keyword argumetns:

  * `n_blocks::Int = 1`: The number of blocks in one transformer unit (containing linear layers and nonlinear layers).
  * `n_linear::Int = 1`: The number of linear `VolumePreservingLowerLayer`s and `VolumePreservingUpperLayer`s in one block.
  * `L::Int = 1`: The number of transformer units.
  * `activation = tanh`: The activation function.
  * `init_upper::Bool = false`: Specifies if the network first acts on the $q$ component.
  * `skew_sym::Bool = false`: specifies if we the weight matrix is skew symmetric or arbitrary.
