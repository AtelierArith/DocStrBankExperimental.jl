get*vertex*neighbours(resource::MBQCResourceState, vertex)

与えられた頂点のMBQCリソース状態における隣接頂点を取得します。

# 引数

  * `resource::MBQCResourceState`: リソースのグラフ表現を含むMBQCリソース状態。
  * `vertex`: 隣接頂点を取得するための頂点。

# 戻り値

指定された頂点の隣接頂点を表す頂点の配列。

# 例

```julia
# MBQCリソース状態を作成
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# 頂点の隣接頂点を取得
vertex = 1
neighbors = get_vertex_neighbours(resource, vertex)
```
