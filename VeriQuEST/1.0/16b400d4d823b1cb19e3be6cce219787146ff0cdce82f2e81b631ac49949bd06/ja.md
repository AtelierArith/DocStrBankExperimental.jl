```
is_vertex_in_graph(resource::MBQCResourceState, vertex::Int64)
```

グラフに頂点が存在するかを確認します。

# 引数

  * `resource::MBQCResourceState`: MBQCリソース状態。
  * `vertex::Int64`: 確認する頂点。

# 戻り値

  * `Bool`: グラフに頂点が存在する場合は`true`、そうでない場合は`false`。

# 例

```julia
is_vertex_in_graph(resource, vertex) # グラフに頂点が存在する場合はtrueを返し、そうでない場合はfalseを返します
```
