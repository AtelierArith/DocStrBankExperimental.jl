```julia
ivertices(genealogy)

```

Return an interable containing the internal vertices of a genealogy.

See also [`leaves`](@ref) for leaves and [`nivertices`](@ref) for the number of leaves and internal vertices.

# Implementation

Default implementations assume that the first `nleaves(genealogy)` vertices are the leaves of the genealogy. If this is the case for your type, you do not need to implement this method.
