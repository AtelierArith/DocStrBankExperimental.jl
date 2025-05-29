```
current_time(valp)
current_time(valp, i)
```

Return the current time in the value provider `valp`. If `is_timeseries(valp)` is [`Timeseries`](@ref), return the vector of timesteps at which the state value is saved. In this case, the two-argument version of the function can also be implemented to efficiently return the time at timestep `i`. By default, the two- argument method calls `current_time(p)[i]`. It is assumed that the timeseries is sorted in increasing order.

If `i` consists of multiple indices (for example, `Colon`, `AbstractArray{Int}`, `AbstractArray{Bool}`) specialized methods may be defined for efficiency. By default, `current_time(valp, ::Colon) = current_time(valp)` to avoid copying the timeseries.

By default, the single-argument version acts as the identity function if `valp isa AbstractVector`.

See: [`is_timeseries`](@ref)
