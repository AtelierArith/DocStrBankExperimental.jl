```
set_vertex_type!(::Client, resource, mg)
```

この関数は、MetaGraphのラウンドタイププロパティに基づいて、頂点タイププロパティを設定します。ラウンドタイプが実装された後に実装する必要があります。

# 引数

  * `client::Client`: Clientオブジェクト。
  * `resource`: グラフとその色付けを含むリソース。
  * `mg`: 頂点タイププロパティが追加されるMetaGraph。

# 例

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_prop!(mg, :round_type, ComputationRound())
set_vertex_type!(client, resource, mg)
```
