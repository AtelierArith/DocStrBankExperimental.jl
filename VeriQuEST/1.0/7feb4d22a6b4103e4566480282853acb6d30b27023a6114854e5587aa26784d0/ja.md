```
add_round_type!(::Client, mg, round_type)
```

この関数は、MBQCモデルのクライアントのメタグラフにラウンドタイプを追加します。指定されたラウンドタイプにメタグラフの`:round_type`プロパティを設定します。

# 引数

  * `::Client`: クライアントオブジェクト。
  * `mg`: プロパティが追加されるメタグラフ。
  * `round_type`: メタグラフに追加されるラウンドタイプ。

# 戻り値

  * 更新されたメタグラフ。

# 例

```julia
client = Client()
mg = MetaGraphs.MetaGraph(graph)
round_type = "round1"
add_round_type!(client, mg, round_type)
```
