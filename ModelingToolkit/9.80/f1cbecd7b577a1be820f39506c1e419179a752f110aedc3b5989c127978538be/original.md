```julia
DiffEqBase.SDEProblemExpr{iip}(sys::AbstractODESystem, u0map, tspan,
                               parammap = DiffEqBase.NullParameters();
                               version = nothing, tgrad = false,
                               jac = false, Wfact = false,
                               checkbounds = false, sparse = false,
                               linenumbers = true, parallel = SerialForm(),
                               kwargs...) where {iip}
```

Generates a Julia expression for constructing an ODEProblem from an ODESystem and allows for automatically symbolically calculating numerical enhancements.
