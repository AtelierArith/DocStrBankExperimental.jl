```
produce_initialised_graph(::Client, mg)
```

この関数は、MBQCモデルのクライアントのためにメタグラフから初期化されたグラフを生成します。単にメタグラフから新しいグラフを作成します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `mg`: グラフに変換されるメタグラフ。

# 戻り値

  * メタグラフから作成された新しいグラフ。

# 例

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
produce_initialised_graph(client, mg)
```
