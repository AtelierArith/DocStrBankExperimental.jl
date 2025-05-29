```julia
DiffEqBase.NonlinearProblemExpr{iip}(sys::NonlinearSystem, u0map,
                                     parammap = DiffEqBase.NullParameters();
                                     jac = false, sparse = false,
                                     checkbounds = false,
                                     linenumbers = true, parallel = SerialForm(),
                                     kwargs...) where {iip}
```

Generates a Julia expression for a NonlinearProblem from a NonlinearSystem and allows for automatically symbolically calculating numerical enhancements.
