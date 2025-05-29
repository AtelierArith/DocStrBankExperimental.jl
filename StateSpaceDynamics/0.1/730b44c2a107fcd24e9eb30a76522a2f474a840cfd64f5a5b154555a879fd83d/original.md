```
fit!(slds::SwitchingLinearDynamicalSystem, y::Matrix{T}; 
     max_iter::Int=1000, 
     tol::Real=1e-12, 
     ) where {T<:Real}
```

Fit a Switching Linear Dynamical System using the variational Expectation-Maximization (EM) algorithm with Kalman smoothing.

# Arguments

  * `slds::SwitchingLinearDynamicalSystem`: The Switching Linear Dynamical System to be fitted.
  * `y::Matrix{T}`: Observed data, size (obs*dim, T*steps).

# Keyword Arguments

  * `max_iter::Int=1000`: Maximum number of EM iterations.
  * `tol::Real=1e-12`: Convergence tolerance for log-likelihood change.

# Returns

  * `mls::Vector{T}`: Vector of log-likelihood values for each iteration.
