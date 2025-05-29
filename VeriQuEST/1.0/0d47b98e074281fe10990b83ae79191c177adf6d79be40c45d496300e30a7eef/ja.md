```
run_verification(::Client, ::Server, round_types, client_resource, state_type)
```

クライアントとサーバー間の検証プロセスを実行します。各ラウンドタイプについて、関数はクライアントメタグラフを生成し、クライアントからグラフと量子レジスタ（qureg）を抽出し、サーバーリソースを作成し、計算を実行し、サーバー上に空の量子状態を初期化し、クライアントメタグラフをリストに保存します。クライアントメタグラフのリストが返されます。

# 引数

  * `::Client`: `Client`インスタンス。
  * `::Server`: `Server`インスタンス。
  * `round_types`: 実行するラウンドのタイプ。
  * `client_resource`: クライアントのリソース。
  * `state_type`: 状態のタイプ。

# 戻り値

  * `Array`: クライアントメタグラフの配列。

# 例

```julia
round_types = ["round1", "round2"]
client_resource = create_resource(Client())
state_type = "state_type_example"
round_graphs = run_verification(Client(), Server(), round_types, client_resource, state_type)
```
