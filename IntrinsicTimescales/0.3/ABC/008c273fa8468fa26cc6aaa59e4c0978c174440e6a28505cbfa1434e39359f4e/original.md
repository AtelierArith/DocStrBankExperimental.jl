```
basic_abc(model::Models.AbstractTimescaleModel; kwargs...)
```

Perform basic ABC rejection sampling.

# Arguments

  * `model::Models.AbstractTimescaleModel`: Model to perform inference on
  * `epsilon::Float64`: Acceptance threshold
  * `max_iter::Integer`: Maximum number of iterations
  * `min_accepted::Integer`: Minimum number of accepted samples required
  * `pmc_mode::Bool=false`: Whether to use PMC proposal distribution
  * `weights=Array{Float64}`: Importance weights (used in PMC mode)
  * `theta_prev=Array{Float64}`: Previous parameters (used in PMC mode)
  * `tau_squared=Array{Float64}`: Covariance matrix (used in PMC mode)
  * `show_progress::Bool=true`: Whether to show progress bar

# Returns

NamedTuple containing:

  * `samples`: All proposed parameters
  * `isaccepted`: Boolean mask of accepted samples
  * `theta_accepted`: Accepted parameters
  * `distances`: Distances for all proposals
  * `n_accepted`: Number of accepted samples
  * `n_total`: Total number of iterations
  * `epsilon`: Acceptance threshold used
  * `weights`: Sample weights (uniform in basic ABC)
  * `tau_squared`: Covariance matrix (zeros in basic ABC)
  * `eff_sample`: Effective sample size
