```
add_flow_vertex!(::Client, mg, resource::MBQCResourceState, flow_type::Union{ForwardFlow,BackwardFlow})
```

この関数は、MBQCモデルのクライアントのメタグラフにフローベルテックスを追加します。最初にフロータイプをシンボルに変換し、次にリソース内の各ベ vertex に対して反復処理を行います。各ベ vertex に対して、検証されたフロー出力を取得し、これをメタグラフのプロパティとして設定します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `mg`: プロパティが追加されるメタグラフ。
  * `resource::MBQCResourceState`: グラフとその色付けを含むリソース。
  * `flow_type::Union{ForwardFlow,BackwardFlow}`: 追加されるフロータイプ。

# 戻り値

  * 更新されたメタグラフ。

# 例

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
flow_type = ForwardFlow()
add_flow_vertex!(client, mg, resource, flow_type)
```
