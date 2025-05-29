```
Particle{T}
```

# フィールド

  * `Θ::Vector{T}`: パラメータのベクトル
  * `accept::Vector{Bool}`: 提案の受け入れ。1: 受け入れ、0: 拒否
  * `weight::Float64`: モデルフィットに基づく粒子の重み（現在の事後対数尤度）
  * `lp::Vector{Float64}`: 各受け入れられた提案に関連する事後確率の対数のベクトル
  * `id::Int`: 粒子のID
