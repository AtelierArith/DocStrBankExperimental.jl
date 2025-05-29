```
function addedge!(graph::Graph{T}, node1::T, node2::T) where T
```

Adds an edge between `node1` and `node2`. If `node1` or `node2` are not present in the `Graph`, they are added.
