```julia
DAEProblemExpr{iip}(sys::AbstractODESystem, u0map, tspan,
                    parammap = DiffEqBase.NullParameters();
                    version = nothing, tgrad = false,
                    jac = false,
                    checkbounds = false, sparse = false,
                    linenumbers = true, parallel = SerialForm(),
                    skipzeros = true, fillzeros = true,
                    simplify = false,
                    kwargs...) where {iip}
```

Generates a Julia expression for constructing a DAEProblem from an ODESystem and allows for automatically symbolically calculating numerical enhancements.
