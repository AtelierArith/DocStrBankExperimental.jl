```
blockdiag(g, h)
```

Return a graph with $|V(g)| + |V(h)|$ vertices and $|E(g)| + |E(h)|$ edges where the vertices and edges from graph `h` are appended to graph `g`.

### Implementation Notes

Preserves the eltype of the input graph. Will error if the number of vertices in the generated graph exceeds the `eltype`.

# Examples

```jldoctest
julia> g1 = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> g2 = SimpleDiGraph([0 1 0; 0 0 1; 1 0 0]);

julia> blockdiag(g1, g2)
{8, 9} directed simple Int64 graph

julia> foreach(println, edges(blockdiag(g1, g2)))
Edge 1 => 2
Edge 2 => 3
Edge 3 => 1
Edge 3 => 4
Edge 4 => 5
Edge 5 => 4
Edge 6 => 7
Edge 7 => 8
Edge 8 => 6
```
