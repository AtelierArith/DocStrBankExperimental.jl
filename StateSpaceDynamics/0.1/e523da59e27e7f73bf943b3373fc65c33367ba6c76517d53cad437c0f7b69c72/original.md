```
loglikelihood(model::GaussianRegressionEmission, Φ::Matrix{<:Real}, Y::Matrix{<:Real})
```

Calculate the log likelihood of the data `Y` given the Gaussian regression emission model and the input features `Φ`.

# Arguments

  * `model::GaussianRegressionEmission`: The Gaussian regression emission model for which to calculate the log likelihood.
  * `Φ::Matrix{<:Real}`: The input features matrix (Observations x Features).
  * `Y::Matrix{<:Real}`: The data matrix (Observations x Features).

# Returns

  * `Vector{Float64}`: A vector of log likelihoods, one for each observation in the data.
