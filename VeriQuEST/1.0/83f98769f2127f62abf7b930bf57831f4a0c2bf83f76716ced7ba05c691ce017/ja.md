```
set_io_qubits_type!(::Client, resource, mg)
```

この関数は、MetaGraphのラウンドタイププロパティに基づいて、MetaGraph内の入出力キュービットタイププロパティを設定します。

# 引数

  * `client::Client`: クライアントオブジェクト。
  * `resource`: グラフとその着色を含むリソース。
  * `mg`: 頂点の入出力タイププロパティが追加されるMetaGraph。

# 例

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_prop!(mg, :round_type, ComputationRound())
set_io_qubits_type!(client, resource, mg)
```
