```
Error(predicate; f="", exception=nothing))
```

An iteration control, as in, `Error(m -> isnan(m.bias), f="Bias overflow!")`. 

If `predicate(m)` is `true`, then log at the `Error` level the value of `f` (or `f(IterationControl.expose(m))` if `f` is a function) and stop iteration at the end of the current control cycle. Here `m` is the object being iterated.

Specify `exception=...` to throw an immediate execption, without waiting to the end of the control cycle.

See also [`Info`](@ref), [`Warn`](@ref). 
