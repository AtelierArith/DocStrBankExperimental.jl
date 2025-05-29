```
union(g, h)
```

Return a graph that combines graphs `g` and `h` by taking the set union of all vertices and edges.

### Implementation Notes

Preserves the eltype of the input graph. Will error if the number of vertices in the generated graph exceeds the eltype.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3); h = SimpleGraph(5);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 1, 3);

julia> add_edge!(h, 3, 4);

julia> add_edge!(h, 3, 5);

julia> add_edge!(h, 4, 5);

julia> f = union(g, h);

julia> collect(edges(f))
5-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 3 => 4
 Edge 3 => 5
 Edge 4 => 5
```
