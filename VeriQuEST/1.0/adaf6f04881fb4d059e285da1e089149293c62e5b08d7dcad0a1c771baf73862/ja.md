```
run_verification(::Client, ::MaliciousServer, round_types, client_resource, state_type, malicious_angles)
```

クライアントが悪意のあるサーバーと対話する文脈で検証プロセスを実行します。このプロセスには、プロパティグラフの生成、グラフと量子レジスタの初期化、サーバーリソースの作成、計算の実行、および空の量子状態の初期化が含まれます。

# 引数

  * `::Client`: この関数がクライアントの文脈で使用されることを示します。
  * `::MaliciousServer`: この関数が悪意のあるサーバーの文脈で使用されることを示します。
  * `round_types::Array`: ラウンドタイプの配列。
  * `client_resource::Dict`: クライアントリソースを含む辞書。
  * `state_type::Symbol`: 量子状態のタイプ。
  * `malicious_angles::Union{Float64,Vector{Float64}}`: 悪意のある行動に使用される角度。

# 例

```julia
round_types = [:round1, :round2, :round3]
client_resource = Dict("env" => create_quantum_env(Client()), "quantum_state" => create_qureg(Client(), 3), "graph" => create_graph(Client(), 3))
state_type = :state1
malicious_angles = [π/4, π/2, 3π/4]
run_verification(Client(), MaliciousServer(), round_types, client_resource, state_type, malicious_angles)
```
