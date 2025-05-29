```julia
DiffEqBase.ODEProblem{iip}(sys::AbstractODESystem, u0map, tspan,
                           parammap = DiffEqBase.NullParameters();
                           version = nothing, tgrad = false,
                           jac = false,
                           checkbounds = false, sparse = false,
                           simplify = false,
                           linenumbers = true, parallel = SerialForm(),
                           kwargs...) where {iip}
```

Generates an ODEProblem from an ODESystem and allows for automatically symbolically calculating numerical enhancements.
