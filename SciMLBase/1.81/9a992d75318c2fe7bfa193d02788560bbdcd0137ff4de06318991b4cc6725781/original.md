```
remake(prob::OptimizationProblem; f = missing, u0 = missing, p = missing,
    lb = missing, ub = missing, int = missing, lcons = missing, ucons = missing,
    sense = missing, kwargs = missing, _kwargs...)
```

Remake the given `OptimizationProblem`. If `u0` or `p` are given as symbolic maps `ModelingToolkit.jl` has to be loaded.
