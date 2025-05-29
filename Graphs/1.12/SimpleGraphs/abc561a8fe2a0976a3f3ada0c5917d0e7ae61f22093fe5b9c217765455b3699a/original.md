```
SimpleGraph(edge_list::Vector)
```

Construct a `SimpleGraph` from a vector of edges. The element type is taken from the edges in `edge_list`. The number of vertices is the highest that is used in an edge in `edge_list`.

### Implementation Notes

This constructor works the fastest when `edge_list` is sorted by the lexical ordering and does not contain any duplicates.

### See also

[`SimpleGraphFromIterator`](@ref)

## Examples

```jldoctest
julia> using Graphs

julia> el = Edge.([ (1, 2), (1, 5) ])
2-element Vector{Graphs.SimpleGraphs.SimpleEdge{Int64}}:
 Edge 1 => 2
 Edge 1 => 5

julia> SimpleGraph(el)
{5, 2} undirected simple Int64 graph
```
