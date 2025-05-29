```
transition_mat(model::MSM; digits::Int64=2)
```

Returns formated table of estimated transition matrix probabilities. It's one of the functions called by the `summary_msm` function.

See also [`summary_msm`](@ref), [`state_coeftable`](@ref), [`coeftable_tvtp`](@ref).
