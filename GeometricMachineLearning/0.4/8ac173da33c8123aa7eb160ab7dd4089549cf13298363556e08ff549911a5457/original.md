```
SymplecticTransformer <: TransformerIntegrator
```

# Constructors

```julia
SymplecticTransformer(sys_dim)
```

Make an instance of `SymplecticTransformer` for a specific system dimension and sequence length. Also see [`LinearSymplecticTransformer`](@ref).

# Arguments

You can provide the additional optional keyword arguments:

  * `n_sympnet::Int = (2)`: The number of sympnet layers in the transformer.
  * `upscaling_dimension::Int = 2*dim`: The upscaling that is done by the gradient layer.
  * `L::Int = 1`: The number of transformer units.
  * `sympnet_activation = tanh`: The activation function for the SympNet layers.
  * `attention_activation = GeometricMachineLearning.MatrixSoftmax()`: The activation function for the Attention layers.
  * `init_upper::Bool=true`: Specifies if the first layer is a $q$-type layer (`init_upper=true`) or if it is a $p$-type layer (`init_upper=false`).
  * `symmetric::Bool=false`:

The number of SympNet layers in the network is `2n_sympnet`, i.e. for `n_sympnet = 1` we have one [`GradientLayerQ`](@ref) and one [`GradientLayerP`](@ref).
