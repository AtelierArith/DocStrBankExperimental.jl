```
getsym(indp, sym)
```

Return a function that takes a value provider and returns the value of the symbolic variable `sym`. If `sym` is not an observed quantity, the returned function can also directly be called with an array of values representing the state vector. `sym` can be an index into the state vector, a symbolic variable, a symbolic expression involving symbolic variables in the index provider `indp`, a parameter symbol, the independent variable symbol, or an array/tuple of the aforementioned. If the returned function is called with a timeseries object, it can also be given a second argument representing the index at which to return the value of `sym`.

At minimum, this requires that the value provider implement [`state_values`](@ref). To support symbolic expressions, the value provider must implement [`observed`](@ref), [`parameter_values`](@ref) and [`current_time`](@ref).

This function typically does not need to be implemented, and has a default implementation relying on the above functions.

If the value provider is a parameter timeseries object, the same rules apply as [`getp`](@ref). The difference here is that `sym` may also contain non-parameter symbols, and the values are always returned corresponding to the state timeseries.
