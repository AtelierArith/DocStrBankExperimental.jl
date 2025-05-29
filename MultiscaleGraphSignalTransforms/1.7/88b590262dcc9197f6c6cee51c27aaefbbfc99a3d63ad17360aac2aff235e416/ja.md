```
lp_ngwp_analysis(G::GraphSig, 𝚽::Matrix{Float64}, W_dual::SparseMatrixCSC{Float64, Int64},
        GP_dual::GraphPart; ϵ::Float64 = 0.3)
```

グラフ信号 `G.f` の LP-NGWP 変換を実行します。

# 入力引数

  * `G::GraphSig`: GraphSig オブジェクト
  * `𝚽::Matrix{Float64}`: グラフラプラシアンの固有ベクトル
  * `W_dual::SparseMatrixCSC{Float64, Int64}`: 双対グラフの重み行列
  * `GP_dual::GraphPart`: 双対グラフの GraphPart オブジェクト

# 出力引数

  * `wavelet_packet::Array{Float64,3}`: ラップされた NGWP 辞書。最初のインデックスは固定レベルでのウェーブレットの選択、2 番目のインデックスはレベル `j` の選択、3 番目のインデックスはウェーブレットベクトル内の要素の選択です。
