```
coeftable_tvtp(model::MSM; digits::Int64=3)
```

Returns formated table of estimated coefficients from TVTP model and their statistics. It's one of the functions called by the `summary_msm` function.

See also [`summary_msm`](@ref), [`state_coeftable`](@ref), [`transition_mat`](@ref).
