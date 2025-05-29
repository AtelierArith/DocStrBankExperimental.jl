```
IEKFMeasurementModel{T,IPM}(measurement::M, R2; nx, ny, Cjac = nothing, step = 1.0, maxiters = 10, epsilon = 1e-8)
```

  * `T` は配列に使用される要素型です
  * `IPM` は測定関数がインプレースであるかどうかを示すブール値です
