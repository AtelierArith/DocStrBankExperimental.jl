```
apply_kraus_map!(::Quest,::TwoQubits,::TracePreserving,ρ,q,complex_mat,num_ops)
```

2つのキュービットの密度行列にKrausマップを適用します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::TwoQubits`: 操作が2つのキュービットに適用されることを示します。
  * `::TracePreserving`: 操作がトレース保存であることを示します。
  * `ρ::QuEST density matrix`: 操作を適用する密度行列です。
  * `q::Tuple{Int64, Int64}`: 操作を適用するキュービットです。
  * `complex_mat::Array{ComplexF64, 4}`: Kraus演算子の配列です。
  * `num_ops::Int64`: Kraus演算子の数です。

# 例

```julia
num_qubits = 2
q = (1, 2)
num_ops = 4
complex_mat = Array{ComplexF64, 4}(undef, 2, 2, 2, num_ops)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
apply_kraus_map!(Quest(),TwoQubits(),TracePreserving(),ρ,q,complex_mat,num_ops)
```
