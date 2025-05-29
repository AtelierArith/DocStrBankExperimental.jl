```
AbstractPolygon{N} <: AbstractPolytope{N}
```

Abstract type for convex polygons (i.e., two-dimensional polytopes).

### Notes

The subtypes of `AbstractPolygon` (including abstract interfaces):

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolygon)
2-element Vector{Any}:
 AbstractHPolygon
 VPolygon
```
