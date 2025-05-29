```
remake(prob::ODEProblem; f = missing, u0 = missing, tspan = missing,
       p = missing, kwargs = missing, _kwargs...)
```

Remake the given `ODEProblem`. If `u0` or `p` are given as symbolic maps `ModelingToolkit.jl` has to be loaded.
