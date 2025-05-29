```
setsym_oop(bi::BatchedInterface)
```

Given a [`BatchedInterface`](@ref) composed from `n` index providers (and corresponding symbols), return a function which takes `n` corresponding value providers and an array of values, and returns an `n`-tuple where each element is a 2-tuple consisting of the updated state values and parameter values of the corresponding value provider. Requires that the value provider implement [`state_values`](@ref), [`parameter_values`](@ref). The updates are performed out-of-place using [`remake_buffer`](@ref).

Note that all of the value providers passed to the returned function must satisfy `is_timeseries(prob) === NotTimeseries()`.

Note that if any subset of the `n` index providers share common symbols (among those passed to `BatchedInterface`) then all of the corresponding value providers in the subset will be updated with the values of the common symbols.

See also: [`is_timeseries`](@ref), [`NotTimeseries`](@ref).
