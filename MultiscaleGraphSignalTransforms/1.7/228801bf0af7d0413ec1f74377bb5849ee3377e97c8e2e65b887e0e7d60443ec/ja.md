```
ngwf_all_vectors(D, 𝚽; σ = 0.2 * maximum(D))
```

全体のNGWF辞書を組み立てます。

# 入力引数

  * `D::Matrix{Float64}`: 固有ベクトルの非自明な距離行列
  * `𝚽::Matrix{Float64}`: グラフラプラシアンの固有ベクトル
  * `σ::Float64`: ガウスウィンドウ幅パラメータ（デフォルト: `0.25 * maximum(D)`）

# 出力引数

  * `𝓤::Matrix{Float64}`: NGWF辞書
