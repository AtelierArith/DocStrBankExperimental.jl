```
difference(g, h)
```

Return a graph with edges in graph `g` that are not in graph `h`.

### Implementation Notes

Note that this function may produce a graph with 0-degree vertices. Preserves the `eltype` of the input graph.

# Examples

```jldoctest
julia> using Graphs

julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> foreach(println, edges(difference(g1, g2)))
Edge 3 => 4
Edge 4 => 5
Edge 5 => 4
```
