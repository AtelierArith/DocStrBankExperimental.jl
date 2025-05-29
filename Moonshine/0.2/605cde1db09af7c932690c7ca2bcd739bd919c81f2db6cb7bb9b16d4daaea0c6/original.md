```julia
leaves(genealogy)

```

Return an interable containing the leaves of a genealogy.

See also [`ivertices`](@ref) for internal vertices and [`nleaves`](@ref) for the number of leaves.

# Implementation

Default implementations assume that the first `nleaves(genealogy)` vertices are the leaves of the genealogy. If this is the case for your type, you do not need to implement this method.
