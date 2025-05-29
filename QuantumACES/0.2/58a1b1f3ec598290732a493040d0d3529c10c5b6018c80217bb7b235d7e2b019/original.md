```
estimate_gate_noise(d::Design, noise_est::NoiseEstimate; kwargs...)
estimate_gate_noise(d_rand::RandDesign, noise_est::NoiseEstimate; kwargs...)
estimate_gate_noise(d::Design, est_eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}, est_covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}, shot_budget::Int; kwargs...)
estimate_gate_noise(d_rand::RandDesign, est_eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}, est_covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}; kwargs...)
```

Returns a [`NoiseEstimate`](@ref) of the gate noise for the design `d` or randomised design `d_rand` derived from estimated circuit eigenvalues, either already contained in a noise estimate `noise_est`, or as estimated circuit eigenvalues `est_eigenvalues_experiment_ensemble` and covariance circuit eigenvalues `est_covariance_experiment_ensemble`, with shot budget `shot_budget`.

# Arguments

  * `d::Design`: Experimental design.
  * `d_rand::RandDesign`: Randomised experimental design.
  * `noise_est::NoiseEstimate`: Noise estimate.
  * `est_eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: Estimated ensemble of circuit eigenvalues.
  * `est_covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}`: Estimated ensemble of covariance circuit eigenvalues.
  * `shot_budget::Int`: Noise estimate shot budget.

# Keword arguments

  * `min_eigenvalue::Float64 = 0.1`: The minimum eigenvalue threshold for clipping.
  * `clip_warning::Bool = true`: Whether to warn if eigenvalues are clipped.
  * `N_warn_split::Integer = 5 * 10^3`: The number of gate eigenvalues above which to warn about splitting.
  * `split::Bool = (d.c.gate_data.N < N_warn_split ? false : true)`: Whether to split the gate eigenvalue projection across gates or simultaneously project all gate eigenvalues.
  * `split_warning::Bool = true`: Whether to warn if the gate eigenvalue projection is not split.
  * `precision::Real = 1e-8`: The solver precision for the gate eigenvalue projection.
