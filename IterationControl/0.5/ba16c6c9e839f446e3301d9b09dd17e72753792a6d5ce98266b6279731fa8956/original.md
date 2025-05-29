```
Warn(predicate; f="")
```

An iteration control, as in, `Warn(m -> length(m.cache) > 100, f="Memory low")`. 

If `predicate(m)` is `true`, then log to `Warn` the value of `f` (or `f(IterationControl.expose(m))` if `f` is a function). Here `m` is the object being iterated.

Can be suppressed by setting the global verbosity level sufficiently low.

See also [`Info`](@ref), [`Error`](@ref). 
