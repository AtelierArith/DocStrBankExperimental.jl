```
is_score_expected(noise_score::NoiseScore, z_score_cutoff::Real)
is_score_expected(noise_score::NoiseScore, z_score_cutoff_lower::Real, z_score_cutoff_upper::Real)
```

指定されたカットオフ内に `noise_score` の z スコアがあるかどうか、また投影が期待通りに z スコアを改善するかどうかを示すブール値を返します。
