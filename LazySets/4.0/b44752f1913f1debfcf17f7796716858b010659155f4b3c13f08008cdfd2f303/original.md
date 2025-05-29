```
AbstractPolyhedron{N} <: ConvexSet{N}
```

Abstract type for closed convex polyhedral sets.

### Notes

See [`HPolyhedron`](@ref) for a standard implementation of this interface.

Every concrete `AbstractPolyhedron` must define the following functions:

  * `constraints_list(::AbstractPolyhedron)` – return a list of all facet constraints

Polyhedra are defined as the intersection of a finite number of closed half-spaces. As such, polyhedra are closed and convex but not necessarily bounded. Bounded polyhedra are called *polytopes* (see [`AbstractPolytope`](@ref)).

The subtypes of `AbstractPolyhedron` (including abstract interfaces):

```jldoctest; setup = :(using LazySets: subtypes)
julia> subtypes(AbstractPolyhedron)
8-element Vector{Any}:
 AbstractPolytope
 HPolyhedron
 HalfSpace
 Hyperplane
 Line
 Line2D
 Star
 Universe
```
