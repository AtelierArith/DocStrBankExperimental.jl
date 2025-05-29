```
diagnose_sstate([point,] model)
```

Run diagnostics on the steady state of the given model. If `point` is not given, then we check the steady state solution stored inside the given model.

Return a tuple of "bad" equations and "bad" variables. 

The set of "bad" equations is one that is inconsistent, i.e. there is no solution. This might happen if the system is overdetermined.

The set of "bad" variables contains variables that cannot be solved uniquely. This might happen if the system is underdetermined. In this case, try adding steady state constraints until you get a unique solution. See [`@steadystate`](@ref ModelBaseEcon.@steadystate) in ModelBaseEcon.

!!! warning "Internal function"
    The output from this function may be difficult to read.<br> Call [`check_sstate`](@ref) instead.

