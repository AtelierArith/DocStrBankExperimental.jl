```
AbstractHPolygon{N} <: AbstractPolygon{N}
```

Abstract type for polygons in constraint representation.

### Notes

See [`HPolygon`](@ref) or [`VPolygon`](@ref) for standard implementations of this interface.

All subtypes must satisfy the invariant that constraints are sorted counter-clockwise.

Every concrete `AbstractHPolygon` must have the following fields:

  * `constraints::Vector{HalfSpace{N, AbstractVector{N}}}` – the constraints

The subtypes of `AbstractHPolygon`:

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractHPolygon)
2-element Vector{Any}:
 HPolygon
 HPolygonOpt
```
