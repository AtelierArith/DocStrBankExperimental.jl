```
SunFlowerGraph(; N = 400)
```

SUNFLOWERGRAPH は N 頂点の単純な重み付きひまわりグラフを構築します。エッジの重みはユークリッド距離の逆数です。

# 入力引数

  * `N::Int64`: デフォルトは 400、頂点の数。N > 26 が必要です。

# 出力引数

  * `G::SimpleWeightedGraph{Int64,Float64}`: ひまわりの単純な重み付きグラフ。
  * `L::Matrix{Float64}`: 重み付き非正規化グラフラプラシアン行列。
  * `X::Matrix{Float64}`: i 番目の行が i 番目のノードの 2D 座標を表す行列。
