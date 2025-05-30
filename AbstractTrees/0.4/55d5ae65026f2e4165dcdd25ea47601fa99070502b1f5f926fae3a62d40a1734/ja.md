```
nextsiblingindex(tree, node_index)
```

ツリー `tree` の `node_index` で指定されたノードの次の兄弟のインデックスを取得します。

次の兄弟が存在しないノードは `nothing` を返すべきです。

**オプション**: [`StoredSiblings`](@ref) 特性を持つインデックス付きツリーはこれを実装する必要があります。
