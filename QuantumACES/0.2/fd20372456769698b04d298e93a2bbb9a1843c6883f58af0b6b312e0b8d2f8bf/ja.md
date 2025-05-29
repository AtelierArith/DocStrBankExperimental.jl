```
ACESData
```

ACESノイズ特性評価実験シミュレーション結果。

# フィールド

  * `d::Design`: 実験デザイン。
  * `noise_est_coll::Matrix{NoiseEstimate}`: 各繰り返しおよび測定予算に対するノイズ推定値。
  * `noise_error_coll::Matrix{NoiseError}`: 各繰り返しおよび測定予算に対するノイズ誤差。
  * `budget_set::Vector{Int}`: 測定予算。
  * `shots_set::Vector{Int}`: `budget_set`の測定予算に対応する測定ショット。
  * `repetitions::Int`: ACESノイズ特性評価実験のシミュレーションの繰り返し回数。
  * `seed::UInt64`: 各繰り返しのためのランダムシードを生成するために使用されるシード。
  * `seeds::Vector{UInt64}`: 各繰り返しのためのシード。
  * `calculation_times::Matrix{Float64}`: 各繰り返しのためにサンプリングをシミュレートし、ゲート固有値を推定して確率シンプレックスに投影するのにかかった時間。
  * `overall_time::Float64`: すべての繰り返しにわたるACESのシミュレーションにかかった全体の時間。
