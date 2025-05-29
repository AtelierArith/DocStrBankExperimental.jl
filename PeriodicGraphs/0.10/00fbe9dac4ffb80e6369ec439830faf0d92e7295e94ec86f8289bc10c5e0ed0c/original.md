```
rings(g::PeriodicGraph{D}, [depth::Integer=15,] symmetries::AbstractSymmetryGroup=NoSymmetryGroup(g), dist::DistanceRecord=DistanceRecord(g,depth)) where D
```

Compute the list of rings in `g`, up to length `2*depth+3`. Return the list of `Vector{Int}` where each sublist is a ring whose vertices are the `reverse_hash_position`s of the sublist elements. Also return an [`AbstractSymmetryGroup`](@ref) acting on the returned rings.

A ring is a cycle of the graph for which there is no shortcut, i.e. no path in the graph between two vertices of the cycle that is shorter than either path connecting the vertices in the cycle.

If provided, `symmetries` should represent the symmetries of the graph as a [`AbstractSymmetryGroup`](@ref) object respecting its documented interface.

A [`PeriodicGraphs.DistanceRecord`](@ref) `dist` can be optionally provided to track the distances between pairs of vertices in the graph.
