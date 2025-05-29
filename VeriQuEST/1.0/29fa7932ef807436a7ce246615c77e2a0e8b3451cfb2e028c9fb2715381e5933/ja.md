```
store_measurement_outcome!(client::Client, client_meta_graph, qubit, outcome)
```

この関数は、特定のキュービットの測定結果をクライアントのメタグラフに保存します。メタグラフ内のプロパティを設定するために `set_p` 関数を使用します。

# 引数

  * `client::Client`: クライアントオブジェクト。
  * `client_meta_graph`: 測定結果が保存されるメタグラフ。
  * `qubit`: 測定結果が保存されるキュービット。
  * `outcome`: 保存される測定結果。

# 戻り値

  * 何も返しません。この関数はクライアント*メタ*グラフをインプレースで変更します。

# 例

```julia
client = Client()
client_meta_graph = MetaGraphs.MetaGraph(graph)
qubit = 1
outcome = 0
store_measurement_outcome!(client, client_meta_graph, qubit, outcome)
```
