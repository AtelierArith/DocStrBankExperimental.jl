```
generate_ou_with_oscillation(theta, dt, duration, num_trials, data_mean, data_var)
```

Generate a one-timescale OU process with an additive oscillation.

# Arguments

  * `theta::Vector{T}`: Parameters [timescale, frequency, coefficient]
  * `dt::Real`: Time step size
  * `duration::Real`: Total time length
  * `num_trials::Integer`: Number of trials
  * `data_mean::Real`: Target mean value
  * `data_var::Real`: Target variance

# Returns

  * Matrix{Float64}: Generated data with dimensions (num*trials, num*timesteps)

# Notes

  * Coefficient is bounded between 0 and 1
  * Combines OU process with sinusoidal oscillation
  * Standardizes and scales output to match target mean and variance
  * Returns NaN matrix if SciML solver fails
