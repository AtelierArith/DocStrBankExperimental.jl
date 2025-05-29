```
estimate_stim_ensemble(d_rand::RandDesign, experiment_shots::Integer; fail_jobs::Vector{Int} = Int[], simulation_seed::Union{UInt64, Nothing} = nothing, ls_type::Symbol = :fgls, split::Bool = false, min_eigenvalue::Real = 0.1)
```

Returns estimated circuit eigenvalues and gate noise estimates from simulated Stim data for the randomised experimental design `d_rand` with `experiment_shots` shots per circuit produced by [`simulate_stim_ensemble`](@ref). Avoids attempting to load failed jobs specified by `fail_jobs`. The simulated data is loaded according to the label implied by the supplied `simulation_seed`, and the estimation procedure uses the least squares estimator `ls_type`, splitting the gate eigenvalue estimator projection across the gates if `split` is `true`, and includes only circuit eigenvalues which are at least `min_eigenvalue`.
