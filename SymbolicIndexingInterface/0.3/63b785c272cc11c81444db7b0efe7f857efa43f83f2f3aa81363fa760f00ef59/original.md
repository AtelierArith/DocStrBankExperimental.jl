```
observed(indp, sym, [states])
```

Return the observed function of the given `sym` in `indp`. The returned function should have the signature `(u, p) -> [values...]` where `u` and `p` is the current state and parameter object, respectively. If `istimedependent(indp) == true`, the function should accept the current time `t` as its third parameter. If `constant_structure(indp) == false`, `observed` accepts a third parameter, which can either be a vector of symbols indicating the order of states or a time index, which identifies the order of states. This function does not need to be defined if [`is_observed`](@ref) always returns `false`. Thus, it is mandatory to always check `is_observed` before using this function.

If `!is_markovian(indp)`, the returned function must have the signature `(u, h, p, t) -> [values...]` where `h` is the history function, which can be called to obtain past values of the state. The exact signature and semantics of `h` depend on how it is used inside the returned function. `h` is obtained from a value provider using [`get_history_function`](@ref).

See also: [`is_time_dependent`](@ref), [`is_markovian`](@ref), [`constant_structure`](@ref).
