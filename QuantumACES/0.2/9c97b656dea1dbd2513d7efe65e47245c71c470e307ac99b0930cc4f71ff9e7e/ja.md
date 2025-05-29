```
calc_ensemble_scaling(d::Design, dist_max::Integer; kwargs...)
calc_ensemble_scaling(d::Design, dist_range::Vector{Int}; kwargs...)
```

デザイン `d` のメリットに対するアンサンブルスケーリングデータを、ノイズモデルのランダムインスタンスに対して [`EnsembleScaling`](@ref) オブジェクトとして返します。これは、これらの距離の関数として、`vertical_dist` および `horizontal_dist` パラメータを持つ回路のためのものです。

# 引数

  * `d::Design`: メリットスケーリングが計算されるデザイン。
  * `dist_max::Int`: メリットスケーリングが計算される最大コード距離。
  * `dist_range::Vector{Int}`: メリットスケーリングが計算されるコード距離。

# キーワード引数

  * `precision::Real = 2e-3`: メリットの推定精度で、平均の標準誤差の目標に対応します。
  * `max_repetitions::Integer = 10000`: メリットが計算される対数正規パウリノイズのランダムインスタンスの最大数。
  * `min_repetitions::Integer = 50`: メリットが計算される対数正規パウリノイズのランダムインスタンスの最小数。
  * `print_repetitions::Integer = 50`: 診断情報を印刷する間の対数正規パウリノイズのランダムインスタンスの数。
  * `seed::Union{UInt64, Nothing} = nothing`: 対数正規パウリノイズのインスタンスを生成するために使用されるシード。
  * `diagnostics::Bool = true`: 診断情報を印刷するかどうか。
  * `save_data::Bool = false`: メリットスケーリングデータを保存するかどうか。
