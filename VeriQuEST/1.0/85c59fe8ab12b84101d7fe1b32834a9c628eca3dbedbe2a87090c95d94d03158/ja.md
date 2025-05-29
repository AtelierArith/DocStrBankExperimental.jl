```
add_correction_vertices!(::Client, mg, resource::MBQCResourceState)
```

この関数は、MBQCモデルのクライアントのメタグラフに修正頂点を追加します。リソース内の各頂点を反復処理し、それぞれの修正頂点を取得し、これらをメタグラフのプロパティとして設定します。

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
add_correction_vertices!(client, mg, resource)
```
