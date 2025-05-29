```
dismantle_ci(g::AGraph, l::Integer, nrem; verbose=false)
```

Applies the Collective Influence (CI) heuristic of Ref. [1]  with distance parameter `l` (tipically `l=3,4`). Removes a maximum of `nrem` vertices from `g`, trying to minimize the size of the maximum connected component of the resulting graph. It stops earlier if the maximum CI goes to zero.

Set `verbose` to `true` for info printing in each iteration.

Returns `(gnew, vmap, remlist)`, where `gnew` is the reduced graph, `vmap` is a vertex map of the vertices of `gnew` to the old ones (see also [`rem_vertices!`](@ref)) and `remlist` contains the removed vertices by removal order.

For more fine grained control see [`dismantle_ci_init`](@ref) and [`dismantle_ci_oneiter!`](@ref).

**Usage**

```julia
g = Graph(100, 1000)
l=3
nrem=10
gnew, vmap, remlist = dismantle_ci(g, l, nrem)

# or equivalently
gnew, heap, lneigs = dismantle_ci_init(g, l)

for it=1:nrem
    irem = dismantle_ci_oneiter!(gnew, heap, lneigs, l)
    irem <= 0 && break
    push!(remlist, irem)
    println("Size Max Component: ", maximum(length, connected_components(g)))
end
vmap = rem_vertices!(gnew, remlist)
```

[1] Morone F., Makse H. Influence maximization in complex networks through optimal percolation. Nature (2015)
