```
eigsROT_Distance(P::Matrix{Float64}, W::SparseMatrixCSC{Float64, Int64}, X::Matrix{Float64}; α::Float64 = 1.0)
```

は、Pの列ベクトルのsROT距離行列を（無重みの）木の上で計算します。

# 入力引数

  * `P::Matrix{Float64}`: 列が同じ総質量を持つベクトル測度の行列。
  * `W::SparseMatrixCSC{Float64, Int64}`: 木の重み行列。
  * `X::Matrix{Float64}`: ノードの位置（i行目はノード`i`の位置を表す）
  * `α::Float64`: デフォルトは1.0。ROTパラメータ。

# 出力引数

  * `dist_sROT::Matrix{Float64}`: 距離行列、dist*sROT[i,j] = d*{sROT}(pᵢ, pⱼ; α)。
  * `Ws::SparseMatrixCSC{Float64, Int64}`: 簡略化された木の重み行列。
  * `Xs::Matrix{Float64}`: 簡略化された木のノード位置
  * `𝚯::Matrix{Float64}`: `P`からの短縮されたpmf。
