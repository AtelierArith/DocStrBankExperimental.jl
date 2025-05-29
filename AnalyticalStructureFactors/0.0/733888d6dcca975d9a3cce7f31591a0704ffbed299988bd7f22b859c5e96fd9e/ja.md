```
phi_to_rho_mixture(ϕ_vector::AbstractVector{T}, σ_vector::AbstractVector{T}) where T<:AbstractFloat
```

コンポーネントのパッキング分率 `ϕ_vector` と直径 `σ_vector` のベクトルを、混合物の対応する数密度 `ρ_vector` のベクトルに変換します。 ρᵢ = 6ϕᵢ / (πσᵢ³)

# 引数

  * `ϕ_vector::AbstractVector{T}`: 各コンポーネントのパッキング分率のベクトル。
  * `σ_vector::AbstractVector{T}`: 各コンポーネントの直径のベクトル。

# 戻り値

  * `Vector{T}`: 各コンポーネントの数密度のベクトル。

# 例外

  * `DimensionMismatch`: `ϕ_vector` と `σ_vector` の長さが一致しない場合。
