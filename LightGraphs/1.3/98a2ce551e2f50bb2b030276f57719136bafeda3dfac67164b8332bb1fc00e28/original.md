```
triangles(g[, v])
triangles(g, vs)
```

Return the number of triangles in the neighborhood of node `v` in graph `g`. If a list of vertices `vs` is specified, return a vector of number of triangles for each node in the list. If no vertices are specified, return the number of triangles for each node in the graph.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(4);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 4);

julia> add_edge!(g, 4, 1);

julia> triangles(g)
4-element Array{Int64,1}:
 1
 1
 0
 1
```
