```
add_output_qubits!(::Client, mg, resource::MBQCResourceState)
```

この関数は、MBQCモデルのクライアントのメタグラフに出力キュービットを追加します。リソースグラフから出力インデックスを取得し、メタグラフの`:output_inds`プロパティをこれらのインデックスに設定します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `mg`: プロパティが追加されるメタグラフ。
  * `resource::MBQCResourceState`: グラフとその着色を含むリソース。

# 戻り値

  * 更新されたメタグラフ。

# 例

```julia
client = Client()
resource = MBQCResourceState(graph)
mg = MetaGraphs.MetaGraph(resource.graph.graph)
add_output_qubits!(client, mg, resource)
```
