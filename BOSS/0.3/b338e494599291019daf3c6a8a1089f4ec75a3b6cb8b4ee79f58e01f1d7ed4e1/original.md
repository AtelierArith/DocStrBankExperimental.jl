```
NonlinModel(; kwargs...)
```

A parametric surrogate model.

If your model is linear, you can use `LinModel` which will provide better performance in the future. (Not yet implemented.)

Define the model as `y = predict(x, θ)` where `θ` are the model parameters.

# Keywords

  * `predict::Function`: The `predict` function according to the definition above.
  * `theta_priors::AbstractVector{<:UnivariateDistribution}`: The prior distributions for the model parameters.
  * `noise_std_priors::NoiseStdPriors`: The prior distributions       of the noise standard deviations of each `y` dimension.
