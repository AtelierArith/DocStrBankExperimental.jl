```
KillAfter(F::Function, args...; timeout::Real=5, verbose::Bool=false, kwargs...)
```

Tries to evaluate a given function `F` before a set `timeout` limit is reached and interrupts the evaluation and returns `nothing` if necessary. NOTE: The given function is evaluated via F(args...; kwargs...).
