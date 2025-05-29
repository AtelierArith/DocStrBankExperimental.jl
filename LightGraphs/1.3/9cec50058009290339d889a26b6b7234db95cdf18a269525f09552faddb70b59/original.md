```
intersect(g, h)
```

Return a graph with edges that are only in both graph `g` and graph `h`.

### Implementation Notes

This function may produce a graph with 0-degree vertices. Preserves the eltype of the input graph.

# Examples

```jldoctest
julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> foreach(println, edges(intersect(g1, g2)))
Edge 1 => 2
Edge 2 => 3
Edge 3 => 1
```
