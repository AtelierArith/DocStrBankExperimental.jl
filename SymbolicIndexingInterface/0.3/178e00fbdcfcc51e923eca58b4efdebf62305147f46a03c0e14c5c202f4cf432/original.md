```
getsym(bi::BatchedInterface)
```

Given a [`BatchedInterface`](@ref) composed from `n` index providers (and corresponding symbols), return a function which takes `n` corresponding value providers and returns an array of the values of the symbols in the union. The returned function can also be passed an `AbstractArray` of the appropriate `eltype` and size as its first argument, in which case the operation will populate the array in-place with the values of the symbols in the union.

Note that all of the value providers passed to the function returned by `getsym` must satisfy `is_timeseries(prob) === NotTimeseries()`.

The value of the `i`th symbol in the union (obtained through `variable_symbols(bi)[i]`) is obtained from the problem corresponding to the associated index provider (i.e. the value provider at index `associated_systems(bi)[i]`).

See also: [`variable_symbols`](@ref), [`associated_systems`](@ref), [`is_timeseries`](@ref), [`NotTimeseries`](@ref).
