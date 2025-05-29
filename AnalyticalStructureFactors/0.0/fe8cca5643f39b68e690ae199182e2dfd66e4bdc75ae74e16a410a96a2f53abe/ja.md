```
S_RPA_mixture_SALR(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                   A_attr_matrix::AbstractMatrix{T}, Z_attr_matrix::AbstractMatrix{T},
                   A_rep_matrix::AbstractMatrix{T}, Z_rep_matrix::AbstractMatrix{T}, 
                   k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

多成分SALR混合物のk値のベクトルに対するRPA部分構造因子行列S_ij(k)を計算します。

# 引数

  * `σ_vector::AbstractVector{T}`: 直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: パッキング分率のベクトル。
  * `A_attr_matrix::AbstractMatrix{T}`: 引力Yukawa成分の振幅Aᵃᵢⱼの行列。
  * `Z_attr_matrix::AbstractMatrix{T}`: 引力Yukawa成分の逆スクリーン長zᵃᵢⱼの行列。
  * `A_rep_matrix::AbstractMatrix{T}`: 斥力Yukawa成分の振幅Aʳᵢⱼの行列。
  * `Z_rep_matrix::AbstractMatrix{T}`: 斥力Yukawa成分の逆スクリーン長zʳᵢⱼの行列。
  * `k_values::AbstractVector{T}`: 波ベクトルの大きさのベクトル。

# 戻り値

  * `Vector{Matrix{T}}`: 各kに対するS*ij(k)行列のベクトル、`k*values`の各kについて1つ。
