```
AbstractCentrallySymmetric{N} <: ConvexSet{N}
```

Abstract type for centrally symmetric compact convex sets.

### Notes

Every concrete `AbstractCentrallySymmetric` must define the following function:

  * `center(::AbstractCentrallySymmetric)` – return the center point

The subtypes of `AbstractCentrallySymmetric`:

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractCentrallySymmetric)
2-element Vector{Any}:
 AbstractBallp
 Ellipsoid
```
