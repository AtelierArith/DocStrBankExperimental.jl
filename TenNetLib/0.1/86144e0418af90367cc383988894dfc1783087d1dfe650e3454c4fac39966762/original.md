```
function getnodes(graph::Graph{T}) where T = copy(graph.nodes)
```

Returns (shallow copy of) nodes in the `Graph`.
