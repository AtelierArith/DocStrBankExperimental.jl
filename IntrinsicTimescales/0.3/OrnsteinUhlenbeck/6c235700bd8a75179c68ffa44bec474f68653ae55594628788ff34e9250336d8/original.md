```
generate_ou_process_sciml(tau, true_D, dt, duration, num_trials, standardize=true)
```

Generate an Ornstein-Uhlenbeck process using DifferentialEquations.jl.

# Arguments

  * `tau::Union{T, Vector{T}}`: Timescale(s) of the OU process
  * `true_D::Real`: Target variance for scaling
  * `dt::Real`: Time step size
  * `duration::Real`: Total time length
  * `num_trials::Integer`: Number of trials/trajectories
  * `standardize::Bool=true`: Whether to standardize output

# Returns

  * `Tuple{Matrix{Float64}, ODESolution}`: 

      * Scaled OU process data
      * Full SDE solution object

# Notes

  * Uses SOSRA solver for efficiency
  * Switches between static and dynamic arrays based on num_trials
  * Standardizes output to match true_D if standardize=true
