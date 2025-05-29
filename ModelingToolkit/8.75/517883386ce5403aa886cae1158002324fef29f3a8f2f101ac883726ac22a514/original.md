```julia
DiffEqBase.NonlinearProblem{iip}(sys::NonlinearSystem, u0map,
                                 parammap = DiffEqBase.NullParameters();
                                 jac = false, sparse = false,
                                 checkbounds = false,
                                 linenumbers = true, parallel = SerialForm(),
                                 kwargs...) where {iip}
```

Generates an NonlinearProblem from a NonlinearSystem and allows for automatically symbolically calculating numerical enhancements.
