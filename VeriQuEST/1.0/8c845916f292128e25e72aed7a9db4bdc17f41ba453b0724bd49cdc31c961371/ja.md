```
get_edge_iterator(resource::MBQCResourceState)
```

MBQCリソース状態のエッジに対するイテレータを取得します。

# 引数

  * `resource::MBQCResourceState`: リソースのグラフ表現を含むMBQCリソース状態。

# 戻り値

リソース状態のグラフのエッジに対するイテレータ。

# 例

```julia
# MBQCリソース状態を作成
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# エッジイテレータを取得
edge_iterator = get_edge_iterator(resource)
```
