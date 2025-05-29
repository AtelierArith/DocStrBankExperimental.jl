```
S_RPA_mixture_Yukawa(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                     A_matrix::AbstractMatrix{T}, Z_matrix::AbstractMatrix{T}, 
                     k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

多成分ユカワ混合物のk値のベクトルに対するRPA部分構造因子行列S_ij(k)を計算します。

# 引数

  * `σ_vector::AbstractVector{T}`: 直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: パッキング分率のベクトル。
  * `A_matrix::AbstractMatrix{T}`: ユカワ振幅Aᵢⱼの行列。
  * `Z_matrix::AbstractMatrix{T}`: ユカワ逆スクリーン長zᵢⱼの行列。
  * `k_values::AbstractVector{T}`: 波ベクトルの大きさのベクトル。

# 戻り値

  * `Vector{Matrix{T}}`: 各kに対するS*ij(k)行列のベクトル、`k*values`の各kに対して1つ。
