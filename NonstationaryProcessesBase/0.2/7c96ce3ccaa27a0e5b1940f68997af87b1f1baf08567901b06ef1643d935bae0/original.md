```
parameterseries(P::Process; p=nothing, times_kwargs...)
```

Return the profiles of a [`Process`](@ref) as parameter values at time indices given by [`times`](@ref). `p` specified the indices of the parameters to return (e.g. 1 or [2, 3]). If `p` is a vector, the values will be returned in an nₚ×nₜ matrix.
