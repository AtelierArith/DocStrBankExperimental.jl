```
get_model_violation(d::Design, noise_est::NoiseEstimate; projected::Bool = false)
get_model_violation(d_rand::RandDesign, noise_est::NoiseEstimate; projected::Bool = false)
get_model_violation(d::Design, noise_est_vector::Vector{NoiseEstimate}; projected::Bool = false)
get_model_violation(d::Design, noise_est_matrix::Matrix{NoiseEstimate}; projected::Bool = false)
```

与えられた設計 `d` または代わりにランダム化設計 `d_rand` に対して、ノイズ推定 `noise_est` に対応する一般化された残差平方和のノイズモデル違反 z スコアを返します。`projected` が `true` の場合、投影ゲート固有値を使用して計算します。
