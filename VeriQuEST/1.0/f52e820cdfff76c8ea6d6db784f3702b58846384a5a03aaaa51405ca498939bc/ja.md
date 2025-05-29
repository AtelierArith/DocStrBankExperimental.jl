```
create_quantum_state(client::Client, state::StateVector, quantum_env, num_qubits)
```

新しい量子状態を状態ベクトルとして作成します。QuEST関数 `createQureg` を使用します。

# 引数

  * `client::Client`: 量子状態が作成されるクライアント。
  * `state::StateVector`: 量子状態が状態ベクトルとして作成されることを示します。
  * `quantum_env`: 量子状態が作成される量子環境。
  * `num_qubits`: 量子状態のキュービット数。

# 戻り値

  * 状態ベクトルとしての新しい量子状態。

# 例

```julia
client = Client()
env = create_quantum_env(client)
state = create_quantum_state(client, StateVector(), env, 2)
```
