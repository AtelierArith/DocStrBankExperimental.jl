```julia
SciMLBase.SteadyStateProblem(sys::AbstractODESystem, u0map,
                             parammap = DiffEqBase.NullParameters();
                             version = nothing, tgrad = false,
                             jac = false,
                             checkbounds = false, sparse = false,
                             linenumbers = true, parallel = SerialForm(),
                             kwargs...) where {iip}
```

Generates an SteadyStateProblem from an ODESystem and allows for automatically symbolically calculating numerical enhancements.
