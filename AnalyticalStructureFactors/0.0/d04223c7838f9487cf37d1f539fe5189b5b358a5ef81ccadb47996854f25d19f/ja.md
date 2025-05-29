```
S_RPA_mixture_Yukawa(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                     k_wavevector::T, 
                     A_matrix::AbstractMatrix{T}, Z_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

多成分混合物の部分構造因子行列 S_ij(k) をランダム位相近似 (RPA) を用いて計算します。参照系は、ヴェルレ・ワイス補正を伴うハードスフェア混合物です。各ペア (i,j) に対する摂動ポテンシャルはユカワ形式であると仮定されています。

使用される RPA の式は次のとおりです: S⁻¹ = (S⁰)⁻¹ - βŨ*scaled ここで βŨ*scaled*ij(k) = √(ρᵢρⱼ) * βũ*Yukawa_ij(k) です。

# 引数

  * `σ_vector::AbstractVector{T}`: 各成分のハードスフェア直径のベクトル（参照系）。
  * `ϕ_vector::AbstractVector{T}`: 各成分の充填率のベクトル（参照系）。
  * `k_wavevector::T`: 波ベクトルの大きさ。
  * `A_matrix::AbstractMatrix{T}`: 各ペア (i,j) に対するユカワ振幅 Aᵢⱼ の行列。Aᵢⱼ は成分 i と j の相互作用の振幅です。
  * `Z_matrix::AbstractMatrix{T}`: 各ペア (i,j) に対するユカワ逆スクリーン長 zᵢⱼ の行列。

# 戻り値

  * `Matrix{T}`: n x n の実数値部分構造因子行列 S_ij(k)。

```
