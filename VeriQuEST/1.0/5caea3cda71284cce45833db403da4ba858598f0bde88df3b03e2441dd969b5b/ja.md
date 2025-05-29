```
apply_kraus_map!(::Quest,::MultipleQubits,::TracePreserving,ρ,leas_sig_qubit,num_qubits,complex_mat,num_ops)
```

複数のキュービットに対して密度行列にクローズマップを適用します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::MultipleQubits`: 操作が複数のキュービットに適用されることを示します。
  * `::TracePreserving`: 操作がトレース保存であることを示します。
  * `ρ::QuEST density matrix`: 操作を適用する密度行列。
  * `leas_sig_qubit::Int64`: 最も重要度の低いキュービット。
  * `num_qubits::Int64`: キュービットの数。
  * `complex_mat::Array{ComplexF64, 3}`: クローズ演算子の配列。
  * `num_ops::Int64`: クローズ演算子の数。

# 例

```julia
num_qubits = 3
leas_sig_qubit = 1
num_ops = 8
complex_mat = Array{ComplexF64, 3}(undef, 2, 2, num_ops)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
apply_kraus_map!(Quest(),MultipleQubits(),TracePreserving(),ρ,leas_sig_qubit,num_qubits,complex_mat,num_ops)
```
