```
merge_vertices(g::AbstractGraph, vs)
```

Create a new graph where all vertices in `vs` have been aliased to the same vertex `minimum(vs)`.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = path_graph(5);

julia> collect(edges(g))
4-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
 Edge 4 => 5

julia> h = merge_vertices(g, [2, 3]);

julia> collect(edges(h))
3-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
```
