```
extract_subset(rng, prefix, t, y, yerr; n_perc=0.03, take_log=true, suffix="")
extract_subset(seed, prefix, t, y, yerr; n_perc=0.03, take_log=true)
```

分析のためにデータのサブセットを抽出し、平均と分散の初期推定値を返します。乱数生成器またはシードを提供できます。

# 引数

  * `seed::Int64` : 乱数生成器のシード。
  * `rng::AbstractRNG` : 乱数生成器。
  * `prefix::String` : 出力ファイルのプレフィックス。
  * `t::Array{Float64,1}` : 時間配列。
  * `y::Array{Float64,1}` : 時系列配列。
  * `yerr::Array{Float64,1}` : 時系列誤差配列。
  * `n_perc::Float64` : 抽出する時系列の割合。
  * `take_log::Bool` : trueの場合、平均と分散の推定のために時系列を対数変換します。
  * `suffix::String` : 出力ファイルのサフィックス。

# 戻り値

  * `t_subset::Array{Float64,1}` : サブセットの時間配列。
  * `y_subset::Array{Float64,1}` : サブセットの時系列配列。
  * `yerr_subset::Array{Float64,1}` : サブセットの時系列誤差配列。
  * `x̄::Float64` : μのための正規分布の平均。
  * `va::Float64` : μのための正規分布の分散。
