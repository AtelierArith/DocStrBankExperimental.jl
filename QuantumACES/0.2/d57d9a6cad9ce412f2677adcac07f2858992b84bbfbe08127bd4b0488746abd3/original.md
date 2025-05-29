```
fit_round_error(rounds_set::Vector{Int}, rounds_memory_errors::Vector{Float64}, rounds_memory_errors_sem::Vector{Float64}; return_cov::Bool = false)
```

Returns parameters for [`round_exponential_model`](@ref) fitted with weighted least squares from the memory errors `rounds_memory_errors` and their standard errors of the mean `rounds_memory_errors_sem` across the rounds in `rounds_set`.
