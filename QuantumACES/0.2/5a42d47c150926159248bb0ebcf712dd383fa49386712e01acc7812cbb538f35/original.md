```
calc_covariance(d::Design; epsilon::Real = 1e-10, weight_time::Bool = true, warning::Bool = true)
calc_covariance(d::Design, gate_eigenvalues::Vector{Float64}; epsilon::Real = 1e-10, weight_time::Bool = true, warning::Bool = true)
calc_covariance(d::Design, eigenvalues_ensemble::Vector{Vector{Float64}}, covariance_ensemble::Vector{Vector{Float64}}; epsilon::Real = 1e-10, weight_time::Bool = true, warning::Bool = true)
calc_covariance(d::Design, eigenvalues_experiment_ensemble::Vector{Vector{Vector{Float64}}}, covariance_experiment_ensemble::Vector{Vector{Vector{Float64}}}; epsilon::Real = 1e-10, weight_time::Bool = true, warning::Bool = true)
```

Returns the circuit eigenvalue estimator covariance matrix for the design `d` with gate eigenvalues `gate_eigenvalues`, eigenvalue ensemble `eigenvalues_ensemble`, and covariance eigenvalue ensemble `covariance_ensemble`. Eigenvalue variances are set to a minimum value `epsilon` and the covariance matrix is adjusted by the times factor if `weight_time` is `true`, and if `warning` is `true`, warns that if `d.full_covariance` is `false` this will only generate the diagonal of the covariance matrix.
