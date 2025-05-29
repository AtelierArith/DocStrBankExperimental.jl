```
S_RPA_mixture_SquareWell(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                         temperature_matrix::AbstractMatrix{T}, 
                         lambda_range_matrix::AbstractMatrix{T}, 
                         k_values::AbstractVector{T}) where {T<:AbstractFloat}
```

多成分スクエアウェル混合物のk値のベクトルに対するRPA部分構造因子行列S_ij(k)を計算します。

# 引数

  * `σ_vector::AbstractVector{T}`: 直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: パッキング分率のベクトル。
  * `temperature_matrix::AbstractMatrix{T}`: 無次元温度Tᵢⱼの行列。
  * `lambda_range_matrix::AbstractMatrix{T}`: スクエアウェル範囲λᵢⱼの行列。
  * `k_values::AbstractVector{T}`: 波ベクトルの大きさのベクトル。

# 戻り値

  * `Vector{Matrix{T}}`: 各kに対するS*ij(k)行列のベクトル、`k*values`の各kに対して1つ。
