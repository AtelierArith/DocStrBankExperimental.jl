```julia
struct PartialPrior{T<:(IncrementalInference.SamplableBelief), P<:Tuple} <: DistributedFactorGraphs.AbstractPrior
```

Partial prior belief (absolute data) on any variable, given `<:SamplableBelief` and which dimensions of the intended variable.

Notes

  * If using [`AMP.ManifoldKernelDensity`](@ref), don't double partial.  Only define the partial in this `PartialPrior` container. 

      * Future TBD, consider using `AMP.getManifoldPartial` for more general abstraction.
