```
add_pauli_noise!(::Quest,::SingleQubit,ρ,q,p)
```

単一キュービットの密度行列にパウリノイズモデルを追加します。

# 引数

  * `::Quest`: この関数がQuest環境の文脈で使用されることを示します。
  * `::SingleQubit`: ノイズが単一のキュービットに適用されることを示します。
  * `ρ::QuEST density matrix`: ノイズを適用する密度行列です。
  * `q::Int64`: ノイズを適用するキュービットです。
  * `p::Tuple{Float64, Float64, Float64}`: X、Y、およびZパウリエラーの確率です。

# 例

```julia
num_qubits = 1
q = 1
p = (0.1, 0.2, 0.3)
quantum_env = createQuESTEnv()
ρ = createDensityQureg(num_qubits, quantum_env)
add_pauli_noise!(Quest(),SingleQubit(),ρ,q,p)
```
