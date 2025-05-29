```
init_qubit_meta_graph!(::Client, ::ComputationRound, resource::MBQCResourceState, mg)
```

この関数は、計算ラウンド中にMBQCモデルのクビットメタグラフをクライアントのために初期化します。メタグラフの各頂点に対して秘密の角度と初期クビットプロパティを設定します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `::ComputationRound`: 計算ラウンドオブジェクト。
  * `resource::MBQCResourceState`: グラフとその着色を含むリソース。
  * `mg`: プロパティが追加されるメタグラフ。

# 例

```julia
client = Client()
round = ComputationRound()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
init_qubit_meta_graph!(client, round, resource, mg)
```
