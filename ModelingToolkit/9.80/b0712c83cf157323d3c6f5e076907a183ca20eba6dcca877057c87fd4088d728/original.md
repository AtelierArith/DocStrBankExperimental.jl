```julia
ImplicitDiscreteFunctionExpr{iip}(sys::ImplicitDiscreteSystem, dvs = states(sys),
                                  ps = parameters(sys);
                                  version = nothing,
                                  kwargs...) where {iip}
```

Create a Julia expression for an `ImplicitDiscreteFunction` from the [`ImplicitDiscreteSystem`](@ref). The arguments `dvs` and `ps` are used to set the order of the dependent variable and parameter vectors, respectively.
