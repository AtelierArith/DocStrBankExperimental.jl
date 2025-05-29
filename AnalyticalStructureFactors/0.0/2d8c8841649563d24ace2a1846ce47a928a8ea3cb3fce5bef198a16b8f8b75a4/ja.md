```
S_RPA_mixture_SALR(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                   k_wavevector::T, 
                   A_attr_matrix::AbstractMatrix{T}, Z_attr_matrix::AbstractMatrix{T},
                   A_rep_matrix::AbstractMatrix{T}, Z_rep_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

多成分混合物の部分構造因子行列 S*ij(k) をランダム位相近似 (RPA) を用いて計算します。参照系は、ヴェルレ・ワイス補正を伴うハードスフェア混合物です。各ペア (i,j) に対する摂動ポテンシャルは SALR 形式であると仮定され、u*SALR = u*Yukawa*attractive - u*Yukawa*repulsive とモデル化されます。

使用される RPA の式は次のとおりです: S⁻¹ = (S⁰)⁻¹ - βŨ*scaled ただし βŨ*scaled*ij(k) = √(ρᵢρⱼ) * βũ*SALR_ij(k) です。

# 引数

  * `σ_vector::AbstractVector{T}`: 各成分のハードスフェア直径のベクトル (参照系)。
  * `ϕ_vector::AbstractVector{T}`: 各成分の充填率のベクトル (参照系)。
  * `k_wavevector::T`: 波ベクトルの大きさ。
  * `A_attr_matrix::AbstractMatrix{T}`: 引力 Yukawa 成分の振幅 Aᵃᵢⱼ の行列。
  * `Z_attr_matrix::AbstractMatrix{T}`: 引力 Yukawa 成分の逆スクリーン長 zᵃᵢⱼ の行列。
  * `A_rep_matrix::AbstractMatrix{T}`: 反発 Yukawa 成分の振幅 Aʳᵢⱼ の行列。
  * `Z_rep_matrix::AbstractMatrix{T}`: 反発 Yukawa 成分の逆スクリーン長 zʳᵢⱼ の行列。

# 戻り値

  * `Matrix{T}`: n x n の実数値部分構造因子行列 S_ij(k)。
