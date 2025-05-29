```julia
SciMLBase.DiscreteFunction{iip}(sys::DiscreteSystem,
                            dvs = unknowns(sys),
                            ps = parameters(sys);
                            kwargs...) where {iip}
```

Create an `DiscreteFunction` from the [`DiscreteSystem`](@ref). The arguments `dvs` and `ps` are used to set the order of the dependent variable and parameter vectors, respectively.
