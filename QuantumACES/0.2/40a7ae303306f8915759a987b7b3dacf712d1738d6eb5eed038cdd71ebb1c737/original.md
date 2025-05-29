```
simulate_aces(d::Design, budget_set::Vector{Int}; kwargs...)
```

Returns simulated ACES noise characterisation experiment results as an [`ACESData`](@ref) object for the experimental design `d` across each of the measurement budgets in `budget_set`.

WARNING: Seeding has the same features as in Stim. The behaviour of the same random seed will differ across different versions of Stim. Also, when measurement shots are sampled in batches, which occurs when `max_samples` is exceeded, the results will differ from when all shots are sampled at once.

# Arguments

  * `d::Design`: Experimental design.
  * `budget_set::Vector{Int}`: Measurement budgets for which to simulate ACES.

# Keyword arguments

  * `repetitions::Integer = 1`: Number of simulation repetitions.
  * `seed::Union{UInt64, Nothing} = nothing`: Seed to use for random number generation.
  * `N_warn::Integer = 10^5`: Number of circuit eigenvalues above which to warn the user about certain keyword argument choices.
  * `max_samples::Integer = 10^9`: Maximum number of Stim samples collected in a single simulation.
  * `min_eigenvalue::Real = 0.1`: Circuit eigenvalues below this threshold are omitted from the estimation procedure.
  * `clip_warning::Bool = false`: Whether to warn the user about clipped eigenvalues.
  * `N_warn_split::Integer = 5 * 10^3`: Number of circuit eigenvalues above which to warn the user about if `split` is false.
  * `split::Bool = (d.c.gate_data.N < N_warn_split ? false : true)`: Whether to split the gate eigenvalue projection across gates or simultaneously project all gate eigenvalues.
  * `precision::Real = 1e-8`: Precision of the solver for projecting noise estimates into the probability simplex.
  * `diagnostics::Bool = true`: Whether to print diagnostics.
  * `detailed_diagnostics::Bool = false`: Whether to print detailed diagnostics for Stim simulations.
  * `save_data::Bool = false`: Whether to save the data.
  * `save_interval::Integer = 50`: Repetition interval at which to save the data.
  * `clear_design::Bool = false`: Whether to clear the saved design data after saving the full simulation data.
