```
add_flow_vertex!(::Client, mg, resource::MBQCResourceState)
```

この関数は、MBQCモデルのクライアントのメタグラフに前方および後方のフローベルティックスを追加します。 `add_flow_vertex!` 関数を2回呼び出し、1回は `ForwardFlow` で、もう1回は `BackwardFlow` で呼び出します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `mg`: プロパティが追加されるメタグラフ。
  * `resource::MBQCResourceState`: グラフとその色付けを含むリソース。

# 戻り値

  * 更新されたメタグラフ。

# 例

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
add_flow_vertex!(client, mg, resource)
```
