```julia
DiffEqBase.OptimizationProblemExpr{iip}(sys::OptimizationSystem,
                                        parammap = DiffEqBase.NullParameters();
                                        u0 = nothing,
                                        grad = false,
                                        hes = false, sparse = false,
                                        checkbounds = false,
                                        linenumbers = true, parallel = SerialForm(),
                                        kwargs...) where {iip}
```

Generates a Julia expression for an OptimizationProblem from an OptimizationSystem and allows for automatically symbolically calculating numerical enhancements.
