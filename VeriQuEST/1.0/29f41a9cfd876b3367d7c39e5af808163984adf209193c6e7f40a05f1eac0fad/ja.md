```
run_computation(client::Client, server::Union{Server,NoisyServer}, client_meta_graph, num_qubits_from_server, server_quantum_state)
```

クライアントの視点からサーバーで計算を実行します。この関数は、サーバーからの量子ビットの数を反復処理し、クライアントのϕを更新し、サーバー上でϕ基準に沿って測定し、クライアントの測定を更新し、測定結果をクライアントに保存します。更新されたクライアントメタグラフが返されます。

# 引数

  * `client::Client`: `Client`インスタンス。
  * `server::Union{Server,NoisyServer}`: `Server`または`NoisyServer`インスタンス。
  * `client_meta_graph`: クライアントのメタグラフ。
  * `num_qubits_from_server`: サーバーからの量子ビットの数。
  * `server_quantum_state`: サーバーの量子状態。

# 戻り値

  * `client_meta_graph`: 更新されたクライアントメタグラフ。

# 例

```julia
client = Client()
server = NoisyServer(noise_model)
client_meta_graph = create_graph(client, 3)
num_qubits_from_server = 3
server_quantum_state = create_quantum_state(server, num_qubits_from_server)
updated_client_meta_graph = run_computation(client, server, client_meta_graph, num_qubits_from_server, server_quantum_state)
```
