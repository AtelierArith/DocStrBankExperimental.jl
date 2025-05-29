```
get_rss(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_rss(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
```

与えられた設計 `d` または代わりにランダム化設計 `d_rand` に対して、ノイズ推定 `noise_est` に対応する一般化残差平方和を返します。`projected` が `true` の場合、投影ゲート固有値を使用して計算します。
