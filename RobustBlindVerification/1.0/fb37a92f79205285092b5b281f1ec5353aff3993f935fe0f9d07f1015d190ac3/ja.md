````
get_number_qubits(resource::MBQCResourceState)

MBQCリソース状態におけるキュービットの数を取得します。

# 引数
- `resource::MBQCResourceState`: リソースのグラフ表現を含むMBQCリソース状態。

# 戻り値
リソース状態におけるキュービットの数。

# 例
```julia
# MBQCリソース状態を作成
graph = MBQCGraph(...)
flow = MBQCFlow(...)
angles = MBQCAngles(...)
resource = MBQCResourceState(graph, flow, angles)

# キュービットの数を取得
num_qubits = get_number_qubits(resource)
```
````
