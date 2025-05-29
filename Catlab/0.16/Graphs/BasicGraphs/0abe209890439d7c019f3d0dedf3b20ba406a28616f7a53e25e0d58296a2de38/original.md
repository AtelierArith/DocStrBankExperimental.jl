Neighbors of vertex in a graph.

In a graph, this function is an alias for [`outneighbors`](@ref); in a symmetric graph, a vertex has the same out-neighbors and as in-neighbors, so the distinction is moot.

In the presence of multiple edges, neighboring vertices are given *with multiplicity*. To get the unique neighbors, call `unique(neighbors(g))`.
