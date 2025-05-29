```
loglikelihood(model::GaussianEmission, Y::Matrix{<:Real})
```

Calculate the log likelihood of the data `Y` given the Gaussian emission model.

# Arguments

  * `model::GaussianEmission`: The Gaussian emission model for which to calculate the log likelihood.
  * `Y::Matrix{<:Real}`: The data matrix, where each row represents an observation.

# Returns

  * `Vector{Float64}`: A vector of log likelihoods, one for each observation in the data.
