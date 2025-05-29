```julia
struct EnsembleProblem{T, T2, T3, T4, T5} <: SciMLBase.AbstractEnsembleProblem
```

Constructor for deprecated usage where a vector of problems is passed directly.

!!! warning
    This constructor is deprecated. Use the standard ensemble syntax with `prob_func` instead.

