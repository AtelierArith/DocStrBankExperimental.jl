```
outdegree(g[, v])
```

Return a vector corresponding to the number of edges which start at each vertex in graph `g`. If `v` is specified, only return degrees for vertices in `v`.

# Examples

```jldoctest
julia> using Graphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> outdegree(g)
3-element Vector{Int64}:
 0
 1
 1
```
