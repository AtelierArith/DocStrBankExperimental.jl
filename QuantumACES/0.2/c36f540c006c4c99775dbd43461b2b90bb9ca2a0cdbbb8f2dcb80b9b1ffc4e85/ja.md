```
get_aic(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_aic(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
```

与えられたデザイン `d` または代わりにランダム化デザイン `d_rand` に対して、ノイズ推定 `noise_est` に対応する赤池情報量基準 (AIC) を返します。`projected` が `true` の場合、投影されたゲート固有値を用いて計算します。
