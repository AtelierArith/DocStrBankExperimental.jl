```
function removeedge!(graph::Graph{T}, node1::T, node2::T) where T
```

Removes the edge between `node1` and `node2`. If `node1` or `node2` are not present in the `Graph`, throws an error. If the edge does not exist, nothing is changed.
