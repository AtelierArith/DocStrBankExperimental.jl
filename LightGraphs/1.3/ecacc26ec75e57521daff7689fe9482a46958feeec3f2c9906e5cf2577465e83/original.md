```
inneighbors(g, v)
```

Return a list of all neighbors connected to vertex `v` by an incoming edge.

### Implementation Notes

Returns a reference to the current graph's internal structures, not a copy. Do not modify result. If the graph is modified, the behavior is undefined: the array behind this reference may be modified too, but this is not guaranteed.

# Examples

```jldoctest
julia> g = SimpleDiGraph([0 1 0 0 0; 0 0 1 0 0; 1 0 0 1 0; 0 0 0 0 1; 0 0 0 1 0]);

julia> inneighbors(g, 4)
2-element Array{Int64,1}:
 3
 5
```
