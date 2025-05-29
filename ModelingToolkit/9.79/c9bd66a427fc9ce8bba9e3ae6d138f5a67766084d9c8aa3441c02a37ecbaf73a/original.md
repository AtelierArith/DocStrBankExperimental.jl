```julia
SciMLBase.NonlinearFunctionExpr{iip}(sys::NonlinearSystem, dvs = unknowns(sys),
                                     ps = parameters(sys);
                                     version = nothing,
                                     jac = false,
                                     sparse = false,
                                     kwargs...) where {iip}
```

Create a Julia expression for a `NonlinearFunction` from the [`NonlinearSystem`](@ref). The arguments `dvs` and `ps` are used to set the order of the dependent variable and parameter vectors, respectively.
