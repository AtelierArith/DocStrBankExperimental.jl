```
function removeedge!(graph::Graph{T}, node1::T, node2::T) where T
```

`node1` と `node2` の間のエッジを削除します。`node1` または `node2` が `Graph` に存在しない場合、エラーが発生します。エッジが存在しない場合、何も変更されません。
