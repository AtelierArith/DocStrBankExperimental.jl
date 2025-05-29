```
function getnodes(graph::Graph{T}) where T = copy(graph.nodes)
```

`Graph`のノードの（浅いコピー）を返します。
