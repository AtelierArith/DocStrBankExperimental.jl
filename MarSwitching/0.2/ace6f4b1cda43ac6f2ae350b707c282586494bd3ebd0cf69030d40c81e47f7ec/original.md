```
state_coeftable(model::MSM, state::Int64; digits::Int64=3)
```

Returns formated table of coefficients and their statistics for a given state.     It's one of the functions called by the `summary_msm` function.

See also [`summary_msm`](@ref), [`coeftable_tvtp`](@ref), [`transition_mat`](@ref).
