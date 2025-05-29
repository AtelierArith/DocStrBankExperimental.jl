```
natural_eigdist(𝚽, 𝛌, Q; α = 1.0, T = :Inf,
                input_format = :zero_measures, distance = :DAG,
                edge_weight = 1, edge_length = 1)
```

グラフラプラシアン固有ベクトル間の自然距離を計算します。

# 入力引数

  * `𝚽::Matrix{Float64}`: （重み付き）グラフラプラシアン固有ベクトルの行列。
  * `𝛌::Vector{Float64}`: 固有値のベクトル。
  * `Q::Matrix{Float64}`: グラフの非重み付き入射行列。
  * `α::Float64`: ROTパラメータ。（デフォルト: `1.0`）
  * `T::Any`: TSDパラメータ、すなわちK_functionalにおける停止時間T（デフォルト: `:Inf`）
  * `input_format::Symbol`: オプション: `:zero_measures`、`:pmf1`および`：pmf2`（デフォルト: `:zero_measures`）
  * `distance::Symbol`: オプション: `:ROT`、`:HAD`、`:DAG`および`:TSD`（デフォルト: `:DAG`）
  * `edg_length::Any`: エッジの長さのベクトル（デフォルト: 1は非重み付きグラフを表します）
  * `edge_weight::Any`: 各エッジの親和性重みを格納する重みベクトル（デフォルト: `1`は非重み付きグラフを表します）。

# 出力引数

  * `dis::Matrix{Float64}`: 距離行列、dis[i,j] = d(𝜙ᵢ₋₁, 𝜙ⱼ₋₁)。
