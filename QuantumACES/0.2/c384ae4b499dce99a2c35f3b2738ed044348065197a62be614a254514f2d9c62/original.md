```
simulate_stim_estimate(d::Design, shots_set::Vector{Int}; kwargs...)
```

Returns simulated estimated circuit eigenvalues, covariance circuit eigenvalues, and corresponding circuit eigenvalue pairs, for the experimental design `d` across each of the measurement shots in `shots_set`.

# Keyword arguments

  * `seed::Union{UInt64, Nothing} = nothing`: Seed controlling the random seeds for Stim.
  * `max_samples::Integer = 10^9`: Maximum number of samples to take in a single Stim simulation.
  * `detailed_diagnostics::Bool = false`: Whether to print diagnostic information about the simulation.
