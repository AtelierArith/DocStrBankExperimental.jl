```
nat_spec_filter(l, D; σ = 0.25 * maximum(D), method = :regular, thres = 0.2)
```

l番目の固有ベクトルを中心に距離行列 `D` を介して自然スペクトルグラフフィルタを構成します。

# 入力引数

  * `l::Int64`: 中心となる固有ベクトルのインデックス
  * `D::Matrix{Float64}`: 固有ベクトルの非自明な距離行列
  * `σ::Float64`: ガウスウィンドウ幅パラメータ（デフォルト: `0.25 * maximum(D)`）
  * `method::Symbol`: `:regular` または `:reduced`（デフォルト: `:regular`）
  * `thres::Float64`: カットオフ閾値 ∈ (0, 1)。

# 出力引数

  * `𝛍::Vector{Float64}`: 自然スペクトルグラフフィルタ
