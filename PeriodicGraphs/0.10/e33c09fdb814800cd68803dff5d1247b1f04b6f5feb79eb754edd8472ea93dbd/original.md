```
PeriodicGraph([nv::Integer, ]edge_list::AbstractVector{PeriodicEdge{N}})
PeriodicGraph{N}([nv::Integer, ]edge_list::AbstractVector{PeriodicEdge{N}})
```

Construct a `PeriodicGraph{N}` from a vector of edges. If `nv` is unspecified, the number of vertices is the highest that is used in an edge in `edge_list`.

### Implementation Notes

This constructor works the fastest when `edge_list` is sorted by the lexical ordering and does not contain any duplicates.

## Examples

```jldoctest
julia> el = PeriodicEdge2D[(1, 1, (1,0)), (1, 3, (0,1)), (3, 1, (0,-1))];

julia> g = PeriodicGraph(el)
PeriodicGraph2D(3, PeriodicEdge2D[(1, 1, (1,0)), (1, 3, (0,1))])

julia> ne(g)
2
```
