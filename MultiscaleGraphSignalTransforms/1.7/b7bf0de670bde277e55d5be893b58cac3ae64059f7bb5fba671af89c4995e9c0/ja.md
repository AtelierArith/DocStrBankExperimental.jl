```
eigDAG_Distance(𝚽, Q, numEigs; edge_weights = 1)
```

ペアワイズグラフラプラシアン固有ベクトル間のDAG距離を計算します。

# 入力引数

  * `𝚽::Matrix{Float64}`: グラフラプラシアン固有ベクトルの行列、𝜙ⱼ₋₁ (j = 1,...,size(𝚽,1)).
  * `Q::Matrix{Float64}`: グラフの入射行列。
  * `numEigs::Int64`: 考慮される固有ベクトルの数。
  * `edge_weight::Any`: デフォルト値は1で、重みなしのグラフを表します（すなわち、すべてのエッジの重みが1に等しい）。重み付きグラフの場合、edge_weightは各エッジの親和性重みを格納する重みベクトルです。

# 出力引数

  * `dis::Matrix{Float64}`: numEigs x numEigsの距離行列、dis[i,j] = d_DAG(𝜙ᵢ₋₁, 𝜙ⱼ₋₁).
