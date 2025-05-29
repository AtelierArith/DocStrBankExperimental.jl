```
UKFMeasurementModel{T,IPM,AUGM}(measurement, R2; nx, ny, ne = nothing, innovation = -, mean = weighted_mean, cov = weighted_cov, cross_cov = cross_cov, static = nothing)
```

  * `T` は配列に使用される要素型です
  * `IPM` は測定関数がインプレースであるかどうかを示すブール値です
  * `AUGM` は測定モデルが拡張されているかどうかを示すブール値です
