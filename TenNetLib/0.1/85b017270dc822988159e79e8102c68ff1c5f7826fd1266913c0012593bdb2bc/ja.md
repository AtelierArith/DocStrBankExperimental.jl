```
function addedge!(graph::Graph{T}, node1::T, node2::T) where T
```

`node1` と `node2` の間にエッジを追加します。`node1` または `node2` が `Graph` に存在しない場合は、追加されます。
