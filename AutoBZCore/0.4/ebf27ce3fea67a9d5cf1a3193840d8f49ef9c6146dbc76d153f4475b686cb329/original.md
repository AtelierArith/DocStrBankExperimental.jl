```
init(::IntegralProblem, ::IntegralAlgorithm; kws...)::IntegralSolver
```

Construct a cache for an [`IntegralProblem`](@ref), [`IntegralAlgorithm`](@ref), and the keyword arguments to the solver (i.e. `abstol`, `reltol`, or `maxiters`) that can be reused for solving the problem for multiple different parameters of the same type.
