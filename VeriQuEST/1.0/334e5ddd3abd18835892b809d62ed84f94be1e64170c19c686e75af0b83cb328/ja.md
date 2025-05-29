```
init_measurement_outcomes!(::Client, mg, resource::MBQCResourceState)
```

この関数は、MBQCモデルのクライアントのメタグラフにおける測定結果を初期化します。リソース内の各頂点を反復処理し、メタグラフ内の各頂点の`:outcome`プロパティを`Int64`に設定します。

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
init_measurement_outcomes!(client, mg, resource)
```
