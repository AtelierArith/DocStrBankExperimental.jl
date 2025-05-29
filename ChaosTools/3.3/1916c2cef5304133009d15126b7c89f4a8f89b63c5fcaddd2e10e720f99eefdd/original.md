```
mean_return_times(ds::DynamicalSystem, u₀, εs, T; kwargs...) → τ, c
```

Return the mean return times `τ`, as well as the amount of returns `c`, for subsets of the state space of `ds` defined by `u₀, εs`. The `ds` is evolved for a maximum of `T` time.

This function is a convenience wrapper around calls to [`exit_entry_times`](@ref) and then to [`transit_return`](@ref) and then some averaging. Thus see [`exit_entry_times`](@ref) for the meaning of `u₀` and `εs` and further info.
