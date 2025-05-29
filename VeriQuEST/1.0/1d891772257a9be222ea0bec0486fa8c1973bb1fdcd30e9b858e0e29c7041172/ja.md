```
init_qubit_meta_graph!(::Client, resource, mg)
```

この関数は、MBQCモデルのクライアントのためにキュービットメタグラフを初期化します。メタグラフからラウンドタイプを取得し、その後、ラウンドタイプに基づいて適切な `init_qubit_meta_graph!` 関数を呼び出します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `resource`: グラフとその色付けを含むリソース。
  * `mg`: プロパティが追加されるメタグラフ。

# 例

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
set_prop!(mg, :round_type, ComputationRound())
init_qubit_meta_graph!(client, resource, mg)
```
