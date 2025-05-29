```
rem_vertices!(g, vs, keep_order=false) -> vmap
```

Remove all vertices in `vs` from `g`. Return a vector `vmap` that maps the vertices in the modified graph to the ones in the unmodified graph. If `keep_order` is `true`, the vertices in the modified graph appear in the same order as they did in the unmodified graph. This might be slower.

### Implementation Notes

This function is not part of the official Graphs API and is subject to change/removal between major versions.

# Examples

```jldoctest
julia> using Graphs

julia> g = complete_graph(5)
{5, 10} undirected simple Int64 graph

julia> vmap = rem_vertices!(g, [2, 4], keep_order=true);

julia> vmap
3-element Vector{Int64}:
 1
 3
 5

julia> g
{3, 3} undirected simple Int64 graph
```
