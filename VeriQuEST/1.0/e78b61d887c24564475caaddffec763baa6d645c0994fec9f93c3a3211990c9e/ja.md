```
init_qubit_meta_graph!(::Client, ::TestRound, resource::MBQCResourceState, mg)
```

この関数は、テストラウンド中にMBQCモデルのクライアントのためにキュビットメタグラフを初期化します。メタグラフ内の各頂点のタイプに基づいて、初期キュビットプロパティを設定します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `::TestRound`: テストラウンドオブジェクト。
  * `resource::MBQCResourceState`: グラフとその色付けを含むリソース。
  * `mg`: プロパティが追加されるメタグラフ。

# 例

```julia
client = Client()
round = TestRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
init_qubit_meta_graph!(client, round, resource, mg)
```
