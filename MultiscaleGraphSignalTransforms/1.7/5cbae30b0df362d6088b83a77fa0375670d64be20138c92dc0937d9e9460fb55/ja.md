```
rngwf_all_vectors(D, 𝚽; σ = 0.2 * maximum(D), thres = 0.2)
```

rNGWF（縮小NGWF）辞書を組み立てます。

# 入力引数

  * `D::Matrix{Float64}`: 固有ベクトルの非自明な距離行列
  * `𝚽::Matrix{Float64}`: グラフラプラシアンの固有ベクトル
  * `σ::Float64`: ガウス窓幅パラメータ（デフォルト: `0.25 * maximum(D)`）
  * `thres::Float64`: カットオフ閾値 ∈ (0, 1)。

# 出力引数

  * `𝓤::Matrix{Float64}`: rNGWF辞書
  * `dic_l2x::Dict`: l-th 中心固有ベクトルによってQRでフィルタリングされた位置を格納する辞書
