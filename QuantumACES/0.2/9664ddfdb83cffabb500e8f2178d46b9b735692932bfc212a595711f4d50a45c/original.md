```
fit_dist_error(dist_set::Vector{Int}, dist_memory_errors::Vector{Float64}, dist_memory_errors_sem::Vector{Float64}; return_cov::Bool = false)
```

Returns parameters for [`dist_linear_model`](@ref) fitted with weighted least squares from the memory errors `dist_memory_errors` and their standard errors of the mean `dist_memory_errors_sem` across the distances in `dist_set`. Note that the fitting is performed in log space: to fit the original parameters, exponentiate the output of [`dist_linear_model`](@ref).
