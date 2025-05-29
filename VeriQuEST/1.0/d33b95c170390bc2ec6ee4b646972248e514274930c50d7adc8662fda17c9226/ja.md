```
get_minimum_vertex_index_flow(resource::MBQCResourceState)
```

与えられた `MBQCResourceState` の最小頂点インデックスフローを取得します。

# 引数

  * `resource::MBQCResourceState`: MBQCリソース状態。

# 戻り値

  * `Int64`: 最小頂点インデックスフロー。

# 例

```julia
min_vertex = get_minimum_vertex_index_flow(resource) # 最小頂点インデックスフローを返します
```
