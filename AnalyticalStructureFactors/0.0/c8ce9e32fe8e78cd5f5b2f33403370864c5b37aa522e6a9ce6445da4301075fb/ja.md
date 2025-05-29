```
Qk_mixture(σ_vector::AbstractVector{T}, ρ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

パーカス-イェビック近似における多成分ハードスフェア混合物のバクスターQ行列を計算します。

`pR`と`pS`の式は、ユーザーが提供した実装に基づいています。

# 引数

  * `σ_vector::AbstractVector{T}`: 各成分のハードスフェア直径のベクトル。
  * `ρ_vector::AbstractVector{T}`: 各成分の数密度のベクトル。
  * `k_wavevector::T`: 波ベクトルの大きさ。

# 戻り値

  * `Matrix{Complex{T}}`: n x n バクスターQ行列。
