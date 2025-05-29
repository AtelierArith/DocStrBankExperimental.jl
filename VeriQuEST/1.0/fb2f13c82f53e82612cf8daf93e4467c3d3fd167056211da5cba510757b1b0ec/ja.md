```
add_depolarising!(::Quest,::TwoQubits,ρ,q,p)
```

2量子ビットの密度行列に脱極化ノイズモデルを追加します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::TwoQubits`: ノイズが2つの量子ビットに適用されることを示します。
  * `ρ::QuEST density matrix`: ノイズを適用する密度行列です。
  * `q::Tuple{Int64, Int64}`: ノイズを適用する量子ビットです。
  * `p::Float64`: ノイズの確率です。

# 例

```julia
num_qubits = 2
q = (1, 2)
p = 0.3
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
add_depolarising!(Quest(),TwoQubits(),ρ,q,p)
```
