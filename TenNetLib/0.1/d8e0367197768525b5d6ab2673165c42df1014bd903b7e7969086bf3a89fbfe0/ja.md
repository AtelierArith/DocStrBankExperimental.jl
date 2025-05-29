```
function nextnode_in_path(graph::Graph{T}, source::T, destination::T, n=1) where T
```

`source` と `destination` の間の最短経路における次のノードを `Graph` から返します。オプションで、経路の `n` 番目の次のノードを見つけます。
