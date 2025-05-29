```
parentindex(tree, node_index)
```

ツリー `tree` のノード `node_index` で指定された親のインデックスを取得します。

親を持たないノード（すなわち、ルートノード）は `nothing` を返すべきです。

**オプション**: [`StoredParents`](@ref) 特性を持つインデックス付きツリーはこれを実装しなければなりません。
