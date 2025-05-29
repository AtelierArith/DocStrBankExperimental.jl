```
mixDamping(ρ::Array{Complex{Float64},2},q::Int64,p::Float64)
```

密度行列にダンピングノイズモデルを混合します。

# 引数

  * `ρ::QuEST 密度行列`: ノイズを適用する密度行列
  * `q::Int64`: ノイズを適用するキュービット
  * `p::Float64`: ノイズの確率

# 例

```julia     num*qubits = 1 q = 1 p = 0.3 quantum*env = createQuESTEnv() ρ = createDensityQureg(num*qubits, quantum*env) add_damping!(Quest(),SingleQubit(),ρ,q,p)

```
