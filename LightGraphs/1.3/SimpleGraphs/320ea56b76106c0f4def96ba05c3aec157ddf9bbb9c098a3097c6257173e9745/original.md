```
SimpleDiGraph(edge_list::Vector)
```

Construct a `SimpleDiGraph` from a vector of edges. The element type is taken from the edges in `edge_list`. The number of vertices is the highest that is used in an edge in `edge_list`.

### Implementation Notes

This constructor works the fastest when `edge_list` is sorted by the lexical ordering and does not contain any duplicates.

### See also

[`SimpleDiGraphFromIterator`](@ref)

## Examples

```jldoctest

julia> el = Edge.([ (1, 3), (1, 5), (3, 1) ])
julia> SimpleDiGraph(el)
{5, 3} directed simple Int64 graph
```
