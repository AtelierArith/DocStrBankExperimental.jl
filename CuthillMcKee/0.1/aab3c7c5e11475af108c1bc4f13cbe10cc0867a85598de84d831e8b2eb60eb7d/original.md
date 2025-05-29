```
 symrcm(adjac, sdegr,[ rev, inv, warnunconnected])
```

Computes the Cuthill-McKee permutation of the graph given as the adjacency list `adjac`. The adjacency list is required to be of type `Vector{Vector{Int}}` such that `adjac[i]` is a vector of the adjacent vertex numbers to vertex `i` in order of ascending vertex degree. The additional required argument `sdegr` is an array of vertex numbers in order of ascending vertex degree. The default is to compute the reverse permutation, i.e. `rev` defaults to `true`. Optionally, when `inv` is set to `true`, the permutation is inverted. Per default the warning displaying the number of unconnected regions in the graph is disabled, to enable, set `warnunconnected` to `true`.
