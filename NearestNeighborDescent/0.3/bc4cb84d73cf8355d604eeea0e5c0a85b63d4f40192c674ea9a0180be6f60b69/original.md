```
local_join!(graph; kwargs...)
```

Perform a local join on each vertex `v`'s neighborhood `N[v]` in `graph`. Given vertex `v` and its neighbors `N[v]`, compute the similarity `graph.metric(p, q)` for each pair `p, q ∈ N[v]` and update `N[q]` and `N[p]`.

This mutates `graph` in-place and returns a nonnegative integer indicating how many neighbor updates took place during the local join.
