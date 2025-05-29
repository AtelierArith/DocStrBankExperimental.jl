```
run_computation(client_meta_graph, num_qubits_from_server, server_quantum_state)
```

サーバーからの各量子ビットに対して新しい `Client` インスタンスを作成することによって計算を実行します。この関数は、サーバーからの量子ビットの数を反復処理し、クライアントの ϕ を更新し、クライアント上で ϕ 基準に沿って測定し、クライアント上で測定を更新し、クライアント上に測定結果を保存します。更新されたクライアントメタグラフが返されます。

# 引数

  * `client_meta_graph`: クライアントのメタグラフ。
  * `num_qubits_from_server`: サーバーからの量子ビットの数。
  * `server_quantum_state`: サーバーの量子状態。

# 戻り値

  * `client_meta_graph`: 更新されたクライアントメタグラフ。

# 例

```julia
client_meta_graph = create_graph(Client(), 3)
num_qubits_from_server = 3
server_quantum_state = create_quantum_state(Client(), num_qubits_from_server)
updated_client_meta_graph = run_computation(client_meta_graph, num_qubits_from_server, server_quantum_state)
```
