```
calc_merit_scaling(d::Design, dist_max::Integer; kwargs...)
calc_merit_scaling(d::Design, dist_range::Vector{Int}; kwargs...)
```

デザイン `d` のメリットスケーリングデータを [`MeritScaling`](@ref) オブジェクトとして返します。これは、これらの距離の関数として、`vertical_dist` および `horizontal_dist` パラメータを持つ回路のためのものです。

# 引数

  * `d::Design`: メリットスケーリングが計算されるデザイン。
  * `dist_max::Int`: メリットスケーリングが計算される最大距離。
  * `dist_range::Vector{Int}`: メリットスケーリングが計算される距離。

# キーワード引数

  * `warning::Bool = true`: ノイズモデルが脱極化していない場合に警告を表示するかどうか。
  * `diagnostics::Bool = true`: 診断情報を表示するかどうか。
  * `save_data::Bool = false`: メリットスケーリングデータを保存するかどうか。
