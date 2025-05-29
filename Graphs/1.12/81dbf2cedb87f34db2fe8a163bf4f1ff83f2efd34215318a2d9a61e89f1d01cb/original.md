```
symmetric_difference(g, h)
```

Return a graph with edges from graph `g` that do not exist in graph `h`, and vice versa.

### Implementation Notes

Note that this function may produce a graph with 0-degree vertices. Preserves the eltype of the input graph. Will error if the number of vertices in the generated graph exceeds the eltype.

# Examples

```jldoctest
julia> using Graphs

julia> g = SimpleGraph(3); h = SimpleGraph(3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(h, 1, 3);

julia> add_edge!(h, 2, 3);

julia> f = symmetric_difference(g, h);

julia> collect(edges(f))
3-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 3
 Edge 2 => 3
```
