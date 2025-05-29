````
get_vertex_iterator(resource::MBQCResourceState)

MBQCリソース状態内の頂点に対するイテレータを取得します。

# 引数
- `resource::MBQCResourceState`: リソースのグラフ表現を含むMBQCリソース状態。

# 戻り値
リソース状態のグラフの頂点に対するイテレータ。

# 例
```julia
# MBQCリソース状態を作成
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# 頂点イテレータを取得
vertex_iterator = get_vertex_iterator(resource)
```
````
