```
set_io_qubits_type!(::TestRound, resource, mg)
```

テストラウンドには古典的な入力はありませんが、このホルダ関数はラウンドに関係なく一方的に呼び出すことを可能にします。すべての頂点に`NoInputQubits`タイプを割り当てます。

# 引数

  * `round::TestRound`: TestRoundオブジェクト。
  * `resource`: グラフとその彩色を含むリソース。
  * `mg`: 頂点のioタイププロパティが追加されるMetaGraph。

# 例

```julia
round = TestRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_io_qubits_type!(round, resource, mg)
```
