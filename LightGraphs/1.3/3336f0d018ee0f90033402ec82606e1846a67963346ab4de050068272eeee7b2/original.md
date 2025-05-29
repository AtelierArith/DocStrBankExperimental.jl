```
neighbors(g, v)
```

Return a list of all neighbors reachable from vertex `v` in `g`. For directed graphs, the default is equivalent to [`outneighbors`](@ref); use [`all_neighbors`](@ref) to list inbound and outbound neighbors.

### Implementation Notes

Returns a reference to the current graph's internal structures, not a copy.  Do not modify result. If the graph is modified, the behavior is undefined:  the array behind this reference may be modified too, but this is not guaranteed.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> neighbors(g, 1)
0-element Array{Int64,1}

julia> neighbors(g, 2)
1-element Array{Int64,1}:
 3

julia> neighbors(g, 3)
1-element Array{Int64,1}:
 1
```
