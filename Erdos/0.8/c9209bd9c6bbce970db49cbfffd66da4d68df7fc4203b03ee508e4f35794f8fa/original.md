```
unsafe_add_edge!(g, u, v)
```

Possibly faster and unsafer version of [`add_edge!`](@ref), which doesn't guarantee some graph invariant properties.

For example, some graph types (e.g. `Graph`) assume sorted adjacency lists as members. In this case order is not preserved while inserting new edges, resulting in a faster construction of the graph. As a consequence though, some functions such `has_edge(g, u, v)` could give incorrect results.

To restore the correct behaviour, call [`rebuild!`](@ref)(g) after the last call to `unsafe_add_edge!`.
