```
qkf_negloglik(params::Vector{T}, data::QKData, N::Int, M::Int) where T<:Real -> Real
```

Compute the negative log-likelihood for a Quadratic Kalman Filter model given parameters and data.

# Arguments

  * `params::Vector{T}`: Vector of model parameters to be converted into a QKModel
  * `data::QKData`: Data container with observations and optional initial conditions
  * `N::Int`: Dimension of the state vector
  * `M::Int`: Dimension of the measurement vector

# Returns

The negative log-likelihood value computed by:

1. Converting parameters to a QKModel
2. Running the Kalman filter
3. Taking the negative sum of the per-period log-likelihoods

# Note

This function is typically used as an objective function for maximum likelihood estimation, where the goal is to minimize the negative log-likelihood.

For optimization, you may want to wrap this function with N, M and data specified:

```julia
negloglik(params) = qkf_negloglik(params, data, N, M)
```
