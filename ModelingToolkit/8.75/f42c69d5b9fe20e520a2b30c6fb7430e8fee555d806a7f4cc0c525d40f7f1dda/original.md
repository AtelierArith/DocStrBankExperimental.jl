```julia
SciMLBase.DiscreteFunction{iip}(sys::DiscreteSystem, dvs = states(sys),
                                ps = parameters(sys);
                                version = nothing,
                                kwargs...) where {iip}
```

Create a `DiscreteFunction` from the [`DiscreteSystem`](@ref). The arguments `dvs` and `ps` are used to set the order of the dependent variable and parameter vectors, respectively.
