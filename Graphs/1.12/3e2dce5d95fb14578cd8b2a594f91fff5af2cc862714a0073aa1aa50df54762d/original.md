```
all_neighbors(g, v)
```

Return a list of all inbound and outbound neighbors of `v` in `g`. For undirected graphs, this is equivalent to both [`outneighbors`](@ref) and [`inneighbors`](@ref).

### Implementation Notes

Returns a reference to the current graph's internal structures, not a copy. Do not modify result. If the graph is modified, the behavior is undefined: the array behind this reference may be modified too, but this is not guaranteed.

# Examples

```jldoctest
julia> using Graphs

julia> g = DiGraph(3);

julia> add_edge!(g, 2, 3);

julia> add_edge!(g, 3, 1);

julia> all_neighbors(g, 1)
1-element Vector{Int64}:
 3

julia> all_neighbors(g, 2)
1-element Vector{Int64}:
 3

julia> all_neighbors(g, 3)
2-element Vector{Int64}:
 1
 2
```
