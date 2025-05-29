```
create_quantum_state(::Server,::StateVector,quantum_env,num_qubits)
```

サーバーのコンテキストで新しい量子状態を作成します。

# 引数

  * `::Server`: この関数がサーバーのコンテキストで使用されることを示します。
  * `::StateVector`: 量子状態が状態ベクトルであることを示します。
  * `quantum_env`: 量子状態が作成されるQuEST環境。
  * `num_qubits`: 量子状態のキュービットの数。

# 例

```julia
create_quantum_state(Server(),StateVector(),quantum_env,num_qubits)
```
