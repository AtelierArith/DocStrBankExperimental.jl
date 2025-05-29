```
loglikelihood(model::PoissonRegressionEmission, Φ::Matrix{<:Real}, Y::Matrix{<:Real}, w::Vector{Float64}=ones(size(Y, 1)))
```

Calculate the log-likelihood of a Poisson regression model.

# Arguments

  * `model::PoissonRegressionEmission`: Poisson regression model.
  * `Φ::Matrix{<:Real}`: Design matrix of shape `(n, input_dim)`.
  * `Y::Matrix{<:Real}`: Response matrix of shape `(n, 1)`.
  * `w::Vector{Float64}`: Weights of the data points. Should be a vector of size `n`.

# Returns

  * `loglikelihood::Float64`: Log-likelihood of the model.
