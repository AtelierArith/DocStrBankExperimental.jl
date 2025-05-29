```
generate_ou_process(tau, true_D, dt, duration, num_trials; standardize=true)
```

Generate an Ornstein-Uhlenbeck process with a single timescale

# Arguments

  * `tau::Union{Real, Vector{<:Real}}`: Timescale(s) of the OU process
  * `true_D::Real`: Target variance for scaling the process
  * `dt::Real`: Time step size
  * `duration::Real`: Total time length
  * `num_trials::Real`: Number of trials/trajectories
  * `standardize::Bool=true`: Whether to standardize output to match true_D

# Returns

  * Matrix{Float64}: Generated OU process data with dimensions (num*trials, num*timesteps)

# Notes

  * Uses generate*ou*process_sciml internally
  * Returns NaN matrix if SciML solver fails
  * Standardizes output to have specified variance if standardize=true
