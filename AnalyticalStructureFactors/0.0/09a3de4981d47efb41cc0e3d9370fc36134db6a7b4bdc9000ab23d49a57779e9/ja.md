```
S_HS_VW_mixture(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

多成分ハードスフェア混合物の部分構造因子行列 S(k) を、Verlet-Weiss (VW) 補正を用いたPercus-Yevick近似で計算します。

# 引数

  * `σ_vector::AbstractVector{T}`: 元のハードスフェア直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: 元の充填率のベクトル。
  * `k_wavevector::T`: 波ベクトルの大きさ。

# 戻り値

  * `Matrix{T}`: VW 補正を含む n x n の実数値部分構造因子行列 S_ij(k)。
