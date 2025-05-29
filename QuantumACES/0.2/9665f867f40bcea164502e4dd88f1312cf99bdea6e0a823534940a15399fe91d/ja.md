```
get_noise_score(noise_error::NoiseError, merit::Merit)
get_noise_score(noise_error_vector::Vector{NoiseError}, merit::Merit)
get_noise_score(noise_error_matrix::Matrix{NoiseError}, merit::Merit)
```

指定された正規化平均二乗誤差 (NRMSE) データの z スコアを含む [`NoiseScore`](@ref) オブジェクトを返します。これは、`noise_error` に与えられたメリット `merit` に基づいています。
