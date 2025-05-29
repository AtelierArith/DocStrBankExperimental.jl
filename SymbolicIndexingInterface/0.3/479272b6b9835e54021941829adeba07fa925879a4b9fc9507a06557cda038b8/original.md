```
setsym(sys, sym)
```

Return a function that takes a value provider and a value, and sets the the state `sym` to that value. Note that `sym` can be an index, a symbolic variable, or an array/tuple of the aforementioned.

Requires that the value provider implement [`state_values`](@ref) and the returned collection be a mutable reference to the state vector in the value provider. Alternatively, if this is not possible or additional actions need to be performed when updating state, [`set_state!`](@ref) can be defined. This function does not work on types for which [`is_timeseries`](@ref) is [`Timeseries`](@ref).
