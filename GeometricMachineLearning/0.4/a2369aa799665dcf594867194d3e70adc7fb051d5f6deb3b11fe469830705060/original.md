```
StandardTransformerIntegrator(sys_dim)
```

Make an instance of `StandardTransformerIntegrator` for a specific system dimension.

Here the standard transformer used as an integrator (see [`TransformerIntegrator`](@ref)). 

It is a composition of [`MultiHeadAttention`](@ref) layers and [`ResNetLayer`](@ref) layers.

# Arguments

The following are optional keyword arguments:

  * `transformer_dim::Int = sys_dim`: this is the dimension *after the upscaling*.
  * `n_blocks::Int = 1` : the number of [`ResNetLayer`](@ref) blocks.
  * `n_heads::Int = sys_dim`: the number of heads in the multihead attention layer.
  * `L::Int = 2`: the number of transformer blocks.
  * `upscaling_activation = identity`: the activation used in the upscaling layer.
  * `resnet_activation = tanh`: the activation used for the [`ResNetLayer`](@ref).
  * `attention_activation = GeometricMachineLearning.VectorSoftmax()` : the activation used for the [`MultiHeadAttention`](@ref) layer.
  * `add_connection:Bool = true`: specifies if the input should be added to the output.
