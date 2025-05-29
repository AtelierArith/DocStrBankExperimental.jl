```
apply_kraus_map!(::Quest,::MultipleQubits,::NotTracePreserving,ρ,q,complex_mat,num_ops)
```

複数のキュービットに対して、トレースを保持しないクラウス写像を密度行列に適用します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::MultipleQubits`: 操作が複数のキュービットに適用されることを示します。
  * `::NotTracePreserving`: 操作がトレースを保持しないことを示します。
  * `ρ::QuEST density matrix`: 操作を適用する密度行列。
  * `q::Tuple{Int64, Int64}`: 最も下位のキュービットとキュービットの数。
  * `complex_mat::Array{ComplexF64, 3}`: クラウス演算子の配列。
  * `num_ops::Int64`: クラウス演算子の数。

# 例

```julia
num_qubits = 3
leas_sig_qubit = 1
num_ops = 8
complex_mat = Array{ComplexF64, 3}(undef, 2, 2, num_ops)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
apply_kraus_map!(Quest(),MultipleQubits(),NotTracePreserving(),ρ,(leas_sig_qubit,num_qubits),complex_mat,num_ops)
```
