```julia
DiffEqBase.DAEProblem{iip}(sys::AbstractODESystem, du0map, u0map, tspan,
                           parammap = DiffEqBase.NullParameters();
                           version = nothing, tgrad = false,
                           jac = false,
                           checkbounds = false, sparse = false,
                           simplify = false,
                           linenumbers = true, parallel = SerialForm(),
                           kwargs...) where {iip}
```

Generates a DAEProblem from an ODESystem and allows for automatically symbolically calculating numerical enhancements.

Note: Solvers for DAEProblems like DFBDF, DImplicitEuler, DABDF2 are  generally slower than the ones for ODEProblems. We recommend trying  ODEProblem and its solvers for your problem first.
