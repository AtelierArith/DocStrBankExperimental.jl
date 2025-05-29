```
eigHAD_Affinity(𝚽, 𝛌; indexEigs = 1:size(𝚽,2))
```

EIGHAD_AFFINITY は、ペアワイズグラフラプラシアン固有ベクトル間のハダマード (HAD) アフィニティを計算します。

# 入力引数

  * `𝚽::Matrix{Float64}`: グラフラプラシアン固有ベクトルの行列、𝜙ⱼ₋₁ (j = 1,...,size(𝚽,1)).
  * `𝛌::Array{Float64}`: 固有値の配列。 (昇順)
  * `indexEigs::Int`: デフォルトはすべての固有ベクトルで、考慮される固有ベクトルのインデックス。

# 出力引数

  * `A::Matrix{Float64}`: numEigs x numEigs アフィニティ行列、A[i,j] = a_HAD(𝜙ᵢ₋₁, 𝜙ⱼ₋₁).
