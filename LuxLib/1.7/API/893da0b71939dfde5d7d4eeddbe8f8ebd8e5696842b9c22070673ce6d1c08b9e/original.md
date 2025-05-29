```
bias_activation(σ, x, bias)
```

Applies the activation function `σ` elementwise to the result of broadcasted addition of `x` and `bias` along the penultimate dimension. A vector `x` is treated as a matrix with a single last dimension.

## Arguments

  * `σ`: Activation function
  * `x`: Input to be transformed
  * `bias`: Bias to be added. Can be `nothing`.

See also [`bias_activation!!`](@ref), [`fast_activation`](@ref).
