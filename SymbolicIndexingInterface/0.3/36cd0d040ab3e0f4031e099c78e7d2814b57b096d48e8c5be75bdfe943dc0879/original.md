```
state_values(valp)
state_values(valp, i)
```

Return an indexable collection containing the values of all states in the value provider `p`. If `is_timeseries(valp)` is [`Timeseries`](@ref), return a vector of arrays, each of which contain the state values at the corresponding timestep. In this case, the two-argument version of the function can also be implemented to efficiently return the state values at timestep `i`. By default, the two-argument method calls `state_values(valp)[i]`. If `i` consists of multiple indices (for example, `Colon`, `AbstractArray{Int}`, `AbstractArray{Bool}`) specialized methods may be defined for efficiency. By default, `state_values(valp, ::Colon) = state_values(valp)` to avoid copying the timeseries.

If this function is called with an `AbstractArray`, it will return the same array.

See: [`is_timeseries`](@ref)
