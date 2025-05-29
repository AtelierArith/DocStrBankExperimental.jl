```
function nextnode_in_path(graph::Graph{T}, source::T, destination::T, n=1) where T
```

Returns the next node in the shortest path between `source` and `destination` in a `Graph`. Optionally, finds `n`th next-node in the path.
