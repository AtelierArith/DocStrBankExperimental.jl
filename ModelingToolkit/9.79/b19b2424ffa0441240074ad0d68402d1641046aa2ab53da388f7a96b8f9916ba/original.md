```julia
SciMLBase.SteadyStateProblemExpr(sys::AbstractODESystem, u0map,
                                 parammap = DiffEqBase.NullParameters();
                                 version = nothing, tgrad = false,
                                 jac = false,
                                 checkbounds = false, sparse = false,
                                 skipzeros = true, fillzeros = true,
                                 linenumbers = true, parallel = SerialForm(),
                                 kwargs...) where {iip}
```

Generates a Julia expression for building a SteadyStateProblem from an ODESystem and allows for automatically symbolically calculating numerical enhancements.
