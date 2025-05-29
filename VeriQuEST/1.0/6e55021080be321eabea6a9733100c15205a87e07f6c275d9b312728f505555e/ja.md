```
mix_two_density_matrices!(::Quest,::DensityMatrices,ρ₁,ρ₂,p)
```

2つの密度行列を与えられた確率で混合します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::DensityMatrices`: この操作が密度行列に適用されることを示します。
  * `ρ₁::QuEST 密度行列`: 最初の密度行列。
  * `ρ₂::QuEST 密度行列`: 2番目の密度行列。
  * `p::Float64`: 混合の確率。

# 例

```julia
num_qubits = 2
quantum_env = createQuESTEnv()
ρ₁ = createDensityQureg(num_qubits, quantum_env)
ρ₂ = createDensityQureg(num_qubits, quantum_env)
p = 0.5
mix_two_density_matrices!(Quest(),DensityMatrices(),ρ₁,ρ₂,p)
```
