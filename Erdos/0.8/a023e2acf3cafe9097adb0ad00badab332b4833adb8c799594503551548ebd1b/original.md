```
strongly_connected_components(g)
```

Compute the strongly connected components of a directed graph `g`.

Return an array of arrays, each of which is the entire connected component.

### Implementation Notes

The order of the components is not part of the API contract.

# Examples

```jldoctest
julia> g = DiGraph([0 1 0; 1 0 1; 0 0 0]);

julia> strongly_connected_components(g)
2-element Array{Array{Int64,1},1}:
 [3]
 [1, 2]
```
