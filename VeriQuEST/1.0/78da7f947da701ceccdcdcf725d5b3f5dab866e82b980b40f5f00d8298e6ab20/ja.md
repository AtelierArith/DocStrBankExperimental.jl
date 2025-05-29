```
add_dephasing!(::Quest,::SingleQubit,ρ,q,p)
```

密度行列に脱相ノイズモデルを追加します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::SingleQubit`: ノイズが単一のキュービットに適用されることを示します。
  * `ρ::QuEST density matrix`: ノイズを適用する密度行列です。
  * `q::Int64`: ノイズを適用するキュービットです。
  * `p::Float64`: ノイズの確率です。

# 例

```julia
num_qubits = 1
q = 1
p = 0.3
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
add_dephasing!(Quest(),SingleQubit(),ρ,q,p) 
```
