```
merge_vertices!(g, vs)
```

Combine vertices specified in `vs` into single vertex whose index will be the lowest value in `vs`. All edges connected to vertices in `vs` connect to the new merged vertex.

Return a vector with new vertex values are indexed by the original vertex indices.

### Implementation Notes

Supports [`SimpleGraph`](@ref) only.

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

julia> merge_vertices!(g, [2, 3])
5-element Array{Int64,1}:
 1
 2
 2
 3
 4

julia> collect(edges(g))
3-element Array{LightGraphs.SimpleGraphs.SimpleEdge{Int64},1}:
 Edge 1 => 2
 Edge 2 => 3
 Edge 3 => 4
```
