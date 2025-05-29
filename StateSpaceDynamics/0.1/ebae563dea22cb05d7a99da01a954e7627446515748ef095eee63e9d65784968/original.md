```
loglikelihood(model::BernoulliRegressionEmission, Φ::Matrix{<:Real}, Y::Matrix{<:Real}, w::Vector{Float64}=ones(size(Y, 1)))
```

Calculate the log likelihood of the data `Y` given the Bernoulli regression emission model and the input features `Φ`. Optionally, a vector of weights `w` can be provided.

# Arguments

  * `model::BernoulliRegressionEmission`: The Bernoulli regression emission model for which to calculate the log likelihood.
  * `Φ::Matrix{<:Real}`: The input features matrix (Observations x Features).
  * `Y::Matrix{<:Real}`: The data matrix (Observations x Features).
  * `w::Vector{Float64}`: A vector of weights corresponding to each observation (defaults to a vector of ones).

# Returns

  * `Vector{Float64}`: A vector of log likelihoods, one for each observation in the data.
