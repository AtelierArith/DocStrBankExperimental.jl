```
common_neighbors(g, u, v)
```

Return the neighbors common to vertices `u` and `v` in `g`.

### Implementation Notes

Returns a reference to the current graph's internal structures, not a copy.  Do not modify result. If the graph is modified, the behavior is undefined:  the array behind this reference may be modified too, but this is not guaranteed. 

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(4);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 4);

julia> add_edge!(g, 4, 1);

julia> add_edge!(g, 1, 3);

julia> common_neighbors(g, 1, 3)
2-element Array{Int64,1}:
 2
 4

julia> common_neighbors(g, 1, 4)
1-element Array{Int64,1}:
 3
```
