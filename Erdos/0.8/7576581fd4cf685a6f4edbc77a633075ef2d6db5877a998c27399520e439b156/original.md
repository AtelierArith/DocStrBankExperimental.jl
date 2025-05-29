```
bipartite_map(g) -> Vector{UInt8}
```

For a bipartite graph `g`, return a vector `c` of size $|V|$ containing the assignment of each vertex to one of the two sets ($c_i == 1$ or $c_i == 2$). If `g` is not bipartite, return an empty vector.

### Implementation Notes

Note that an empty vector does not necessarily indicate non-bipartiteness. An empty graph will return an empty vector but is bipartite.

# Examples

```jldoctest
julia> using LightGraphs

julia> g = SimpleGraph(3);

julia> bipartite_map(g)
3-element Array{UInt8,1}:
 0x01
 0x01
 0x01

julia> add_vertices!(g, 3);

julia> add_edge!(g, 1, 2);

julia> add_edge!(g, 2, 3);

julia> bipartite_map(g)
3-element Array{UInt8,1}:
 0x01
 0x02
 0x01
```
