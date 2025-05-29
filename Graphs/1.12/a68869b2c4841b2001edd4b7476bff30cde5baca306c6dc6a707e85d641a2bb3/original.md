```
induced_subgraph(g, vlist)
induced_subgraph(g, elist)
```

Return the subgraph of `g` induced by the vertices in  `vlist` or edges in `elist` along with a vector mapping the new vertices to the old ones (the  vertex `i` in the subgraph corresponds to the vertex `vmap[i]` in `g`.)

The returned graph has `length(vlist)` vertices, with the new vertex `i` corresponding to the vertex of the original graph in the `i`-th position of `vlist`.

### Usage Examples

```doctestjl
julia> g = complete_graph(10)

julia> sg, vmap = induced_subgraph(g, 5:8)

julia> @assert g[5:8] == sg

julia> @assert nv(sg) == 4

julia> @assert ne(sg) == 6

julia> @assert vm[4] == 8

julia> sg, vmap = induced_subgraph(g, [2,8,3,4])

julia> @assert sg == g[[2,8,3,4]]

julia> elist = [Edge(1,2), Edge(3,4), Edge(4,8)]

julia> sg, vmap = induced_subgraph(g, elist)

julia> @assert sg == g[elist]
```
