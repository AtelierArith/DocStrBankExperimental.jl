```
S_HS_VW_mixture(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

VW修正部分構造因子行列 S_ij(k) を k 値のベクトルに対して計算します。

# 引数

  * `σ_vector::AbstractVector{T}`: 元の直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: 元の充填率のベクトル。
  * `k_values::AbstractVector{T}`: 波ベクトルの大きさのベクトル。

# 戻り値

  * `Vector{Matrix{T}}`: 各 k に対して 1 つの S*ij(k) 行列を持つベクトル。
