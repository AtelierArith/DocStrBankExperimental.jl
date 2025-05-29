```
reverse(g)
```

Return a directed graph where all edges are reversed from the original directed graph.

### Implementation Notes

Preserves the eltype of the input graph.

# Examples

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> foreach(println, edges(reverse(g)))
Edge 1 => 3
Edge 2 => 1
Edge 3 => 2
Edge 4 => 3
Edge 4 => 5
Edge 5 => 4
```
