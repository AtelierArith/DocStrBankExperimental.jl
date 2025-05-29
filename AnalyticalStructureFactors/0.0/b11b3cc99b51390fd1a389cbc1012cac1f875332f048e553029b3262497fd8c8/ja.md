```
S_RPA_mixture_SquareWell(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                         temperature_matrix::AbstractMatrix{T}, 
                         lambda_range_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

多成分スクエアウェル混合物のRPA部分構造因子行列S_ij(k)を計算する関数`f(k)`を返します。システムとポテンシャルのパラメータは固定されています。

# 引数

  * `σ_vector::AbstractVector{T}`: ハードスフェア直径のベクトル。
  * `ϕ_vector::AbstractVector{T}`: パッキング分率のベクトル。
  * `temperature_matrix::AbstractMatrix{T}`: 無次元温度Tᵢⱼの行列。
  * `lambda_range_matrix::AbstractMatrix{T}`: スクエアウェル範囲λᵢⱼの行列。

# 戻り値

  * `Function`: 波ベクトル`k`を受け取り、S_ij(k)行列を返す関数。
