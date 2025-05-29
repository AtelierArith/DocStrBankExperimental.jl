```
EnsembleScaling
```

実験デザインのためのアンサンブルスケーリングデータで、垂直および水平方向の距離パラメータを持つ回路のランダムノイズモデルの下で。

# フィールド

  * `d::Design`: スケーリングデータが計算されるデザイン。
  * `dist_range::Vector{Int}`: 回路の距離。
  * `merits::Vector{Merit}`: 各距離に対するデザインのメリット。
  * `merit_ensemble::Vector{Vector{Merit}}`: 各距離に対するランダムノイズモデル全体でのデザインのメリット。
  * `seeds::Vector{UInt64}`: ランダムノイズパラメータのためのシード。
  * `calculation_times::Matrix{Float64}`: デザインを生成し、脱偏光メリットを計算し、メリットアンサンブルを計算するための時間、各距離に対して。
  * `overall_time::Float64`: メリットアンサンブルスケーリングデータを計算するのにかかった全体の時間。
