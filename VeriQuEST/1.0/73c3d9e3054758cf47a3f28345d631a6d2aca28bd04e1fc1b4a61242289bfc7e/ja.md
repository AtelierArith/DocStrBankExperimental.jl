```
produce_initialised_qureg(client::Client, mg)
```

この関数は、MBQCモデルのクライアントのためにメタグラフから量子状態を取得します。`get_prop`関数を使用して、メタグラフから`:quantum_state`プロパティを取得します。

# 引数

  * `client::Client`: クライアントオブジェクト。
  * `mg`: 量子状態が取得されるメタグラフ。

# 戻り値

  * メタグラフの量子状態。

# 例

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
produce_initialised_qureg(client, mg)
```
