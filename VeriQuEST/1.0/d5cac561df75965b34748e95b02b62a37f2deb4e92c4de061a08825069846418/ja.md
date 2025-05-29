```
run_verification(client::Client, server::NoisyServer, round_types, client_resource, state_type)
```

クライアントとノイジーサーバー間の検証プロセスを実行します。各ラウンドタイプについて、クライアントのプロパティグラフを生成し、クライアントからグラフと量子レジスタを抽出し、サーバーのためのリソースを作成し、計算を実行し、サーバーのために空の量子状態を初期化し、クライアントのメタグラフを保存します。すべてのクライアントメタグラフのリストを返します。

# 引数

  * `client::Client`: 検証プロセスに参加する`Client`インスタンス。
  * `server::NoisyServer`: 検証プロセスに参加する`NoisyServer`インスタンス。
  * `round_types`: 検証プロセスで実行されるラウンドのタイプ。
  * `client_resource`: クライアントに利用可能なリソース。
  * `state_type`: 検証プロセスで使用される状態のタイプ。

# 戻り値

  * `Array`: 各ラウンドタイプのクライアントメタグラフの配列。

# 例

```julia
client = Client()
server = NoisyServer(noise_model)
round_types = [ComputationRound(), TestRound()]
client_resource = create_resource(client, client_graph, client_qureg)
state_type = :state1
round_graphs = run_verification(client, server, round_types, client_resource, state_type)
```
