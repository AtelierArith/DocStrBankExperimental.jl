```
get_bic(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_bic(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
```

与えられたデザイン `d` または代わりにランダム化デザイン `d_rand` に対して、ノイズ推定 `noise_est` に対応するベイズ情報基準 (BIC) を返します。`projected` が `true` の場合、投影されたゲート固有値を用いて計算します。
