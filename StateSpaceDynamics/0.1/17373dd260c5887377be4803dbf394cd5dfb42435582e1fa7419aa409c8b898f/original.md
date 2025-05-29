```
estep(lds::LinearDynamicalSystem{S,O}, y::Array{T,3}) where {T<:Real, S<:GaussianStateModel{T}, O<:AbstractObservationModel{T}}
```

Perform the E-step of the EM algorithm for a Linear Dynamical System, treating all input as multi-trial.

# Arguments

  * `lds::LinearDynamicalSystem{S,O}`: The Linear Dynamical System struct
  * `y::Array{T,3}`: Observed data, size (obs*dim, T*steps, n*trials)   Note: For single-trial data, use y[1:1, :, :] to create a 3D array with n*trials = 1

# Returns

  * `E_z::Array{T,3}`: Expected latent states, size (state*dim, state*dim, T*steps, n*trials)
  * `E_zz::Array{T,4}`: Expected z*t * z*t', size (state*dim, state*dim, T*steps, n*trials, state_dim)
  * `E_zz_prev::Array{T,4}`: Expected z*t * z*{t-1}', size (state*dim, state*dim, T*steps, n*trials, state_dim)
  * `x_smooth::Array{T,3}`: Smoothed state estimates, size (state*dim, state*dim, T*steps, n*trials)
  * `p_smooth::Array{T,4}`: Smoothed state covariances, size (state*dim, state*dim, T*steps, n*trials, state_dim)
  * `ml::T`: Total marginal likelihood (log-likelihood) of the data across all trials

# Note

  * This function first smooths the data using the `smooth` function, then computes sufficient statistics.
  * It treats all input as multi-trial, with single-trial being a special case where n_trials = 1.
