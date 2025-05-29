Return Matrix{Vector{Vector{Int}}} of all shortest paths. First index is src, second is tgt, and it points to a vector of all shortest paths, represented as a sequence of edge indices.

Shortest path to self is empty.  [Vector{Int}()]

An empty Vector at i, j represents there being no path i -> j.
