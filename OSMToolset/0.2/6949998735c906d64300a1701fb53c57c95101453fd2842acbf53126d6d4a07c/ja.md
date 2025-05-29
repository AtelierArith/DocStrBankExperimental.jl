```
findnode(sindex::NodeSpatIndex, point::Union{LLA, ENU})
```

`sindex` 空間インデックス内で、与えられた `point` 座標に最も近いノードを見つけます。

`distance` と `nodeid` の名前付きタプルを返します。`sindex` の `node_range` 内にノードが見つからない場合、`nodeid` は `0` に、`distance` は `Inf` に設定されます。
