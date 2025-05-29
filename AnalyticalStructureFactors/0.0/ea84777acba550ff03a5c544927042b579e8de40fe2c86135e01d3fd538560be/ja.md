```
IS_HS_VW_mixture(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, k_wavevector::T) where {T<:AbstractFloat}
```

多成分ハードスフェリック混合物の部分構造因子行列 S⁻¹(k) の逆行列を、Verlet-Weiss 補正を伴う Percus-Yevick 近似を使用して計算します。

# 引数

  * `σ_vector::AbstractVector{T}`: 元のハードスフェア直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: 元の充填率のベクトル。
  * `k_wavevector::T`: 波ベクトルの大きさ。

# 戻り値

  * `Matrix{Complex{T}}`: VW 補正を伴う n x n 逆構造因子行列 S⁻¹_ij(k)。
