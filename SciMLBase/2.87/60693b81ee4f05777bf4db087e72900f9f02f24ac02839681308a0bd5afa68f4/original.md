```
remake(prob::NonlinearProblem; f = missing, u0 = missing, p = missing,
    problem_type = missing, kwargs = missing, _kwargs...)
```

Remake the given `NonlinearProblem`. If `u0` or `p` are given as symbolic maps `ModelingToolkit.jl` has to be loaded.
