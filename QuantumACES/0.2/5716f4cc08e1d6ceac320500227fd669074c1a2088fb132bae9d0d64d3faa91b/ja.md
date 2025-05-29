```
calc_covariance(d::Design, noise_est::NoiseEstimate; weight_time::Bool = false)
calc_covariance(d_rand::RandDesign, noise_est::NoiseEstimate; weight_time::Bool = false)
```

デザイン `d` またはランダム化デザイン `d_rand` に関連するノイズ推定 `noise_est` の推定共分散行列を返します。`weight_time` が `true` の場合、ショット予算を時間要因で重み付けします。
