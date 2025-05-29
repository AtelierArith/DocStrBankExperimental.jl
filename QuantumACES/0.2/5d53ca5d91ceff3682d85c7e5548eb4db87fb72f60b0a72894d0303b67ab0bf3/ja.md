```
get_noise_error(d::Design, noise_est::NoiseEstimate)
get_noise_error(d_rand::RandDesign, noise_est::NoiseEstimate)
```

[`NoiseError`](@ref) オブジェクトを返し、`noise_est` におけるゲートノイズ推定値と設計 `d` の真のゲート固有値に対する正規化平方根平均二乗誤差 (NRMSE) を含みます。あるいは、ランダム化された設計 `d_rand` に対しても同様です。
