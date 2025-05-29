```
indegree(g[, v])
```

Return a vector corresponding to the number of edges which end at each vertex in graph `g`. If `v` is specified, only return degrees for vertices in `v`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> indegree(g)
3-element Array{Int64,1}:
 1
 0
 1
```
