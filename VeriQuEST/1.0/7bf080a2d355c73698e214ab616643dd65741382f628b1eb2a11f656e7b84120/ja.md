```
is_vertex_in_graph(resource::MBQCResourceState, novertex::Nothing)
```

グラフに頂点が存在するか確認します。

# 引数

  * `resource::MBQCResourceState`: MBQCリソース状態。
  * `novertex::Nothing`: 確認する頂点。

# 戻り値

  * グラフに頂点が存在する場合は `true`、そうでない場合は `false`。

# 例

```julia
is_vertex_in_graph(resource, novertex) # グラフに頂点が存在する場合はtrueを返し、そうでない場合はfalseを返します
```
