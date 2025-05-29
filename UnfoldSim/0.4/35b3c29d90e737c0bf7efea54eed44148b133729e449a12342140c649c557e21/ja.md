```
LogNormalOnset <: AbstractOnset
```

対数正規分布を使用したイベント間距離（サンプル単位）の対数正規分布（[コードと数学的参照](https://juliastats.org/Distributions.jl/stable/univariate/#Distributions.LogNormal)）。

大きな `μ` および `σ` の値には注意してください。これらは対数スケールであるためです。σ>8はすぐにメモリ不足の信号を生成する可能性があります！  ヒント: イベント間距離のサンプルを手動で生成するには、[`simulate_interonset_distances`](@ref) 関数を使用してください。

# フィールド

  * `μ`: 対数変換された変数の平均（対数正規乱数変数の対数は正規分布に従います）。
  * `σ`: 対数変換された変数の標準偏差。
  * `offset = 0`（オプション）: イベント間の最小距離。
  * `truncate_upper = nothing`（オプション）: 分布が切り捨てられる上限（サンプル単位）。

# 例

```julia-repl
julia> onset_distribution = LogNormalOnset(3, 0.25, 10, 25)
LogNormalOnset
  μ: Int64 3
  σ: Float64 0.25
  offset: Int64 10
  truncate_upper: Int64 25
```

他にも [`UniformOnset`](@ref)、[`NoOnset`](@ref) を参照してください。
