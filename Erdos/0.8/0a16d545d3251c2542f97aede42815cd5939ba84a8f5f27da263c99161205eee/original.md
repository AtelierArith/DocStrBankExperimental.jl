```
subgraph(g, vlist) -> sg, vlist
subgraph(g, elist) -> sg, vlist
```

Returns the subgraph of `g` induced by the vertices in  `vlist` or by the edges in `elist`, along with `vlist` itself (a newly created vector for the second method).

The returned graph has `length(vlist)` vertices, with the new vertex `i` corresponding to the vertex of the original graph in the `i`-th position of `vlist`.

For easy subgraph creation also `g[vlist]` or `g[elist]` can be used.

If `g` is a network, vector and edge properties won't be converved `sg`. You can preserve properties using the [`subnetwork`](@ref) method.

### Usage Examples:

```julia
g = CompleteGraph(10)
sg, vlist = subgraph(g, 5:8)
@assert g[5:8] == sg
@assert nv(sg) == 4
@assert ne(sg) == 6
@assert vm[4] == 8

sg, vlist = subgraph(g, [2,8,3,4])
@asssert sg == g[[2,8,3,4]]

elist = [Edge(1,2), Edge(3,4), Edge(4,8)]
sg, vlist = subgraph(g, elist)
@asssert sg == g[elist]
```
