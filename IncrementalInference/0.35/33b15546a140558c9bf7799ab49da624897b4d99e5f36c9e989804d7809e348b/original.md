```julia
mutable struct PriorCircular{T<:(IncrementalInference.SamplableBelief)} <: DistributedFactorGraphs.AbstractPrior
```

Introduce direct observations on all dimensions of a Circular variable:

## Example:

```julia
PriorCircular( MvNormal([10; 10; pi/6.0], diagm([0.1;0.1;0.05].^2)) )
```

Related

[`Circular`](@ref), [`Prior`](@ref), [`PartialPrior`](@ref)
