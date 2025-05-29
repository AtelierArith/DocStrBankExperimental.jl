```
loglikelihood(model::AutoRegressionEmission, Y_prev::Matrix{<:Real}, Y::Matrix{<:Real})
```

Calculate the log likelihood of the data `Y` given the autoregressive emission model and the previous observations `Y_prev`.

# Arguments

  * `model::AutoRegressionEmission`: The autoregressive emission model for which to calculate the log likelihood.
  * `Y_prev::Matrix{<:Real}`: The matrix of previous observations, where each row represents an observation.
  * `Y::Matrix{<:Real}`: The data matrix, where each row represents an observation.

# Returns

  * `Vector{Float64}`: A vector of log likelihoods, one for each observation in the data.
