```
sample(model::PoissonRegressionEmission, Φ::Matrix{<:Real}; n::Int=size(Φ, 1))
```

Generate `n` samples from a Poisson regression model. Returns a matrix of size `(n, 1)`.

# Arguments

  * `model::PoissonRegressionEmission`: Poisson regression model.
  * `Φ::Matrix{<:Real}`: Design matrix of shape `(n, input_dim)`.
  * `n::Int=size(Φ, 1)`: Number of samples to generate.

# Returns

  * `Y::Matrix{<:Real}`: Matrix of samples of shape `(n, 1)`.
