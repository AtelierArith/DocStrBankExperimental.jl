```
run_computation(::Client, ::MaliciousServer, server_resource, client_meta_graph, num_qubits_from_server, server_quantum_state)
```

悪意のあるサーバーと対話するクライアントのコンテキストで量子計算を実行します。この計算は、位相角の更新、特定の基準に沿った測定、および測定結果の保存を含みます。

# 引数

  * `::Client`: この関数がクライアントのコンテキストで使用されることを示します。
  * `::MaliciousServer`: この関数が悪意のあるサーバーのコンテキストで使用されることを示します。
  * `server_resource::Dict`: サーバーリソースを含む辞書。
  * `client_meta_graph::Graph`: クライアントのメタグラフ。
  * `num_qubits_from_server::Int64`: サーバーから受け取ったキュービットの数。
  * `server_quantum_state::QuEST object`: サーバーの量子状態。

# 例

```julia
server_resource = Dict("env" => create_quantum_env(Server()), "quantum_state" => create_qureg(Server(), 3), "graph" => create_graph(Server(), 3), "angles" => [π/4, π/2, 3π/4])
client_meta_graph = create_graph(Client(), 3)
num_qubits_from_server = 3
server_quantum_state = create_qureg(Server(), 3)
run_computation(Client(), MaliciousServer(), server_resource, client_meta_graph, num_qubits_from_server, server_quantum_state)
```
