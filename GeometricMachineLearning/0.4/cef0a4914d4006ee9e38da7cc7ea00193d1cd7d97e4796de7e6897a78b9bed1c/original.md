```
LinearSymplecticTransformer(sys_dim, seq_length)
```

Make an instance of `LinearSymplecticTransformer` for a specific system dimension and sequence length.

# Arguments

You can provide the additional optional keyword arguments:

  * `n_sympnet::Int = (2)`: The number of sympnet layers in the transformer.
  * `upscaling_dimension::Int = 2*dim`: The upscaling that is done by the gradient layer.
  * `L::Int = 1`: The number of transformer units.
  * `activation = tanh`: The activation function for the SympNet layers.
  * `init_upper::Bool=true`: Specifies if the first layer is a $q$-type layer (`init_upper=true`) or if it is a $p$-type layer (`init_upper=false`).

The number of SympNet layers in the network is `2n_sympnet`, i.e. for `n_sympnet = 1` we have one [`GradientLayerQ`](@ref) and one [`GradientLayerP`](@ref).
