```
vertex_cover(g, DegreeVertexCover())
```

Obtain a vertex cover using a greedy heuristic.

### Implementation Notes

An edge is said to be covered if it has at least one end-point in the vertex cover. Initialise the vertex cover to an empty set and iteratively choose the vertex with the most uncovered edges.

### Performance

Runtime: O((|V|+|E|)*log(|V|)) Memory: O(|V|)

# Examples

```jldoctest
julia> using Graphs

julia> vertex_cover(path_graph(3), DegreeVertexCover())
1-element Vector{Int64}:
 2

julia> vertex_cover(cycle_graph(3), DegreeVertexCover())
2-element Vector{Int64}:
 1
 3
```
