```
setsym(bi::BatchedInterface)
```

Given a [`BatchedInterface`](@ref) composed from `n` index providers (and corresponding symbols), return a function which takes `n` corresponding problems and an array of the values, and updates each of the problems with the values of the corresponding symbols.

Note that all of the value providers passed to the function returned by `setsym` must satisfy `is_timeseries(prob) === NotTimeseries()`.

Note that if any subset of the `n` index providers share common symbols (among those passed to `BatchedInterface`) then all of the corresponding value providers in the subset will be updated with the values of the common symbols.

See also: [`is_timeseries`](@ref), [`NotTimeseries`](@ref).
