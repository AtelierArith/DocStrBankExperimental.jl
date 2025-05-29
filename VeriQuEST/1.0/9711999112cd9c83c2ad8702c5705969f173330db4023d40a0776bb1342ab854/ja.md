```
MetaGraph(::Client, resource::MBQCResourceState)
```

この関数は、指定されたMBQCResourceStateからMetaGraphを作成します。リソース状態からグラフを抽出し、それをMetaGraphでラップします。

# 引数

  * `client::Client`: クライアントオブジェクト。
  * `resource::MBQCResourceState`: グラフを含むMBQCリソース状態。

# 例

`julia client = Client() resource = MBQCResourceState(graph) MetaGraph(client, resource)``
