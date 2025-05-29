```
S_RPA_mixture_Yukawa(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                     A_matrix::AbstractMatrix{T}, Z_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

多成分Yukawa混合物のRPA部分構造因子行列S_ij(k)を計算する関数`f(k)`を返します。システムとポテンシャルのパラメータは固定されています。

# 引数

  * `σ_vector::AbstractVector{T}`: ハードスフェア直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: パッキング分率のベクトル。
  * `A_matrix::AbstractMatrix{T}`: Yukawa振幅Aᵢⱼの行列。
  * `Z_matrix::AbstractMatrix{T}`: Yukawa逆スクリーン長zᵢⱼの行列。

# 返り値

  * `Function`: 波ベクトル`k`を受け取り、S_ij(k)行列を返す関数。
