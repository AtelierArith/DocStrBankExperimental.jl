```
set_io_qubits_type!(::ComputationRound, resource, mg)
```

計算ラウンドでは、時々キュービットの入力値があります。これが発生した場合、この関数はプロパティグラフにそれらのためのスペースを割り当てます。入力インデックスにある頂点には `InputQubits` タイプが割り当てられ、残りには `NoInputQubits` が割り当てられます。

# 引数

  * `round::ComputationRound`: ComputationRound オブジェクト。
  * `resource`: グラフとその彩色を含むリソース。
  * `mg`: 頂点の io タイププロパティが追加される MetaGraph。

# 例

```julia
round = ComputationRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_io_qubits_type!(round, resource, mg)
```
