```
eigROT_Distance(P, Q; edge_length = 1, α = 1.0)
```

は、グラフ上の P の列ベクトルの ROT 距離行列を計算します。

# 入力引数

  * `P::Matrix{Float64}`: 同じ総質量を持つベクトル測定の列を持つ行列。
  * `Q::SparseMatrixCSC{Int64,Int64}`: グラフの非加重インシデンス行列。
  * `edge_length::Any`: 長さベクトル（デフォルト: 1 は非加重グラフを表す）
  * `α::Float64`: デフォルトは 1.0。ROT パラメータ。

# 出力引数

  * `dis::Matrix{Float64}`: 距離行列、dis[i,j] = d_{ROT}(pᵢ, pⱼ; α)。

```
