```
MeritScaling
```

垂直および水平距離パラメータを持つ回路の実験デザインのためのスケーリングデータ、通常は脱偏極ノイズの下で。

# フィールド

  * `d::Design`: スケーリングデータが計算されるデザイン。
  * `dist_range::Vector{Int}`: 回路の距離。
  * `merits::Vector{Merit}`: 一連の距離に対するデザインのメリット。
  * `calculation_times::Matrix{Float64}`: 各距離に対してデザインを生成し、メリットを計算するのにかかる時間。
  * `overall_time::Float64`: 脱偏極ノイズのためのメリットスケーリングデータを計算するのにかかる全体の時間。
