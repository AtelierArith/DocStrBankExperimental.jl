```
apply_kraus_map!(::Quest,::SingleQubit,::TracePreserving,ρ,q,complex_mat,num_ops)
```

単一キュービットの密度行列にKrausマップを適用します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::SingleQubit`: 操作が単一のキュービットに適用されることを示します。
  * `::TracePreserving`: 操作がトレース保存であることを示します。
  * `ρ::QuEST density matrix`: 操作を適用する密度行列。
  * `q::Int64`: 操作を適用するキュービット。
  * `complex_mat::Array{ComplexF64, 3}`: Kraus演算子の配列。
  * `num_ops::Int64`: Kraus演算子の数。

# 例

```julia
num_qubits = 1
q = 1
num_ops = 2
complex_mat = Array{ComplexF64, 3}(undef, 2, 2, num_ops)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
apply_kraus_map!(Quest(),SingleQubit(),TracePreserving(),ρ,q,complex_mat,num_ops)
```
