```
strong_rings([rs::Vector{Vector{Int}},] g::PeriodicGraph{D}, [depth::Integer=15,] symmetries::AbstractSymmetryGroup=NoSymmetryGroup(g), dist::DistanceRecord=DistanceRecord(g,depth)) where D
```

Compute the list of strong rings in `g`, up to length `2*depth+3`. Return them with their symmetry group. Each ring is represented by the list of [`hash_position`](@ref) of its vertices.

The optional first argument `rs` is the list of rings which can be provided if previously computed.

See [`rings`](@ref) for the meaning of the other arguments.

A strong ring is a cycle of the graph which cannot be decomposed into a sum of any number of smaller cycles. By comparison, a ring is a cycle which cannot be decomposed into a sum of two smaller cycles. In particular, all strong rings are rings.

See also [`strong_erings`](@ref) to obtain the rings as a list of integers representing the edges of the ring, instead of a list of integers representing its vertices.
