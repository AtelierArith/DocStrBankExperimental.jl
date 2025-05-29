```
AbstractPolytope{N} <: AbstractPolyhedron{N}
```

Abstract type for compact convex polytopic sets.

### Notes

See [`HPolytope`](@ref) or [`VPolytope`](@ref) for standard implementations of this interface.

Every concrete `AbstractPolytope` must define the following method:

  * `vertices_list(::AbstractPolytope)` – return a list of all vertices

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolytope)
5-element Vector{Any}:
 AbstractCentrallySymmetricPolytope
 AbstractPolygon
 HPolytope
 Tetrahedron
 VPolytope
```

A polytope is a bounded polyhedron (see [`AbstractPolyhedron`](@ref)). Polytopes are compact convex sets with either of the following equivalent properties:

1. They are the intersection of a finite number of closed half-spaces.
2. They are the convex hull of finitely many vertices.
