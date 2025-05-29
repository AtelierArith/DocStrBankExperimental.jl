```
S_HS_VW_mixture(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}) where {T<:AbstractFloat}
```

多成分ハードスフェア混合物のVW修正部分構造因子行列S(k)を計算する関数`f(k)`を返します。システムパラメータは固定されています。

# 引数

  * `σ_vector::AbstractVector{T}`: 元のハードスフェア直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: 元の充填率のベクトル。

# 返り値

  * `Function`: 波ベクトル`k`を受け取り、S_ij(k)行列を返す関数。
