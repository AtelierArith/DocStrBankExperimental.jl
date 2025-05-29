```
sample(model::GaussianRegressionEmission, Φ::Matrix{<:Real}; n::Int=size(Φ, 1))
```

Generate `n` samples from a Gaussian regression model. Returns a matrix of size `(n, output_dim)`.

# Arguments

  * `model::GaussianRegressionEmission`: Gaussian regression model.
  * `Φ::Matrix{<:Real}`: Design matrix of shape `(n, input_dim)`.
  * `n::Int=size(Φ, 1)`: Number of samples to generate.

# Returns

  * `Y::Matrix{<:Real}`: Matrix of samples of shape `(n, output_dim)`.
