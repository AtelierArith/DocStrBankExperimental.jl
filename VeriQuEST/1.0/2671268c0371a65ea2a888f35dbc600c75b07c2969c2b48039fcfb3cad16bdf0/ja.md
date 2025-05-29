```
set_io_qubits_type!(::MBQC, resource, mg)
```

この関数は、盲目なしのMBQCのMetaGraphにおける入力/出力キュービットタイププロパティを設定します。入力インデックスにある頂点には`InputQubits`タイプが割り当てられ、残りには`NoInputQubits`が割り当てられます。

# 引数

  * `client::MBQC`: MBQCクライアントオブジェクト。
  * `resource`: グラフとその着色を含むリソース。
  * `mg`: 頂点のioタイププロパティが追加されるMetaGraph。

# 例

```julia
client = MBQC()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_io_qubits_type!(client, resource, mg)
```
