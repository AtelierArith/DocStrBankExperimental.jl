```
degree(g[, v])
```

Return a vector corresponding to the number of edges which start or end at each vertex in graph `g`. If `v` is specified, only return degrees for vertices in `v`. For directed graphs, this value equals the incoming plus outgoing edges. For undirected graphs, it equals the connected edges.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> degree(g)
3-element Array{Int64,1}:
 1
 1
 2
```
