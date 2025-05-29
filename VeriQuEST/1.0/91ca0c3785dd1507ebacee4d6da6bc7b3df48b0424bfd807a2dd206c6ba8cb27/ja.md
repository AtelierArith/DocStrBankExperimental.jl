```
init_qubit_meta_graph!(::Client, mbqc::MBQC, resource::MBQCResourceState, mg)
```

この関数は、MBQCモデルにおけるクライアントのためのキュビットメタグラフを初期化します。メタグラフの各頂点に対して、秘密の角度と初期キュビットプロパティを設定します。

# 引数

  * `client::Client`: クライアントオブジェクト。
  * `mbqc::MBQC`: MBQCオブジェクト。
  * `resource::MBQCResourceState`: グラフとその彩色を含むリソース。
  * `mg`: プロパティが追加されるメタグラフ。

# 例

```julia
client = Client()
mbqc = MBQC()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
init_qubit_meta_graph!(client, mbqc, resource, mg)
```
