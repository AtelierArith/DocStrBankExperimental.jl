```
S_RPA_mixture_SquareWell(σ_vector::AbstractVector{T}, ϕ_vector::AbstractVector{T}, 
                         k_wavevector::T, 
                         temperature_matrix::AbstractMatrix{T}, 
                         lambda_range_matrix::AbstractMatrix{T}) where {T<:AbstractFloat}
```

多成分混合物の部分構造因子行列 S_ij(k) をランダム位相近似 (RPA) を用いて計算します。参照系は、ヴェルレ・ワイス補正を伴うハードスフェア混合物です。各ペア (i,j) に対する摂動ポテンシャルは、スクエアウェル形式であると仮定されています。

使用される RPA の式は次のとおりです: S⁻¹ = (S⁰)⁻¹ - βŨ*scaled ここで βŨ*scaled*ij(k) = √(ρᵢρⱼ) * βũ*SquareWell_ij(k) です。

# 引数

  * `σ_vector::AbstractVector{T}`: 各成分のハードスフェア直径のベクトル (参照系)。
  * `ϕ_vector::AbstractVector{T}`: 各成分のパッキング分率のベクトル (参照系)。
  * `k_wavevector::T`: 波ベクトルの大きさ。
  * `temperature_matrix::AbstractMatrix{T}`: 各ペア (i,j) に対する無次元温度 Tᵢⱼ の行列。                                         Tᵢⱼ は通常、井戸の深さ εᵢⱼ に関連しています (例: k*B * T*abs / εᵢⱼ)。
  * `lambda_range_matrix::AbstractMatrix{T}`: 各ペア (i,j) に対するスクエアウェル範囲 λᵢⱼ の行列                                           (参照成分のハードスフェア直径 σ または σᵢⱼ の単位で)。

# 戻り値

  * `Matrix{T}`: n x n の実数値部分構造因子行列 S_ij(k)。
