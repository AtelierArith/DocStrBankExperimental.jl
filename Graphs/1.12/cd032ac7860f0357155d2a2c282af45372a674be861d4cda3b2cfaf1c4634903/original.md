```
a_star(g, s, t[, distmx][, heuristic][, edgetype_to_return])
```

Compute a shortest path using the [A* search algorithm](http://en.wikipedia.org/wiki/A%2A_search_algorithm).

Return a vector of edges.

# Arguments

  * `g::AbstractGraph`: the graph
  * `s::Integer`: the source vertex
  * `t::Integer`: the target vertex
  * `distmx::AbstractMatrix`: an optional (possibly sparse) `n × n` matrix of edge weights. It is set to `weights(g)` by default (which itself falls back on [`Graphs.DefaultDistance`](@ref)).
  * `heuristic`: an optional function mapping each vertex to a lower estimate of the remaining distance from `v` to `t`. It is set to `v -> 0` by default (which corresponds to Dijkstra's algorithm). Note that the heuristic values should have the same type as the edge weights!
  * `edgetype_to_return::Type{E}`: the type `E<:AbstractEdge` of the edges in the return vector. It is set to `edgetype(g)` by default. Note that the two-argument constructor `E(u, v)` must be defined, even for weighted edges: if it isn't, consider using `E = Graphs.SimpleEdge`.

!!! warning
    Since a two-argument edge constructor `E(u, v)` is used to construct the path, metadata associated with the edge (like its weight) will be lost in the result. You might need to code a post-processing step yourself.

