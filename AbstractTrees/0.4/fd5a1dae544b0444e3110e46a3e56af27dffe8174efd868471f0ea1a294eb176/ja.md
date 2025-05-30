```
prevsiblingindex(tree, node_index)
```

ツリー `tree` のノード `node_index` で指定されたノードの前の兄弟のインデックスを取得します。

前の兄弟が存在しないノードは `nothing` を返すべきです。

**オプション**: [`StoredSiblings`](@ref) を持つインデックス付きツリーはこれを実装できますが、組み込みのツリーアルゴリズムでは必要ありません。
