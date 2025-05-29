```
Info(f=identity)
```

An iteration control, as in, `Info(my_loss_function)`. 

Log to `Info` the value of `f(m)`, where `m` is the object being iterated. If `IterativeControl.expose(m)` has been overloaded, then log `f(expose(m))` instead.

Can be suppressed by setting the global verbosity level sufficiently low. 

See also [`Warn`](@ref), [`Error`](@ref). 
