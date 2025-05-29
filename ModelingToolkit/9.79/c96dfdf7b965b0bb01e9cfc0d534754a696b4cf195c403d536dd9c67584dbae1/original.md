```julia
DiffEqBase.OptimizationProblem{iip}(sys::OptimizationSystem, u0map,
                                    parammap = DiffEqBase.NullParameters();
                                    grad = false,
                                    hess = false, sparse = false,
                                    cons_j = false, cons_h = false,
                                    checkbounds = false,
                                    linenumbers = true, parallel = SerialForm(),
                                    kwargs...) where {iip}
```

Generates an OptimizationProblem from an OptimizationSystem and allows for automatically symbolically calculating numerical enhancements.

Certain solvers require setting `cons_j`, `cons_h` to `true` for constrained-optimization problems.
