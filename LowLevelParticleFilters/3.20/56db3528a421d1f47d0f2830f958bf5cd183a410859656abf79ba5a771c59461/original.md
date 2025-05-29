```
UKFMeasurementModel{T,IPM,AUGM}(measurement, R2; nx, ny, ne = nothing, innovation = -, mean = weighted_mean, cov = weighted_cov, cross_cov = cross_cov, static = nothing)
```

  * `T` is the element type used for arrays
  * `IPM` is a boolean indicating if the measurement function is inplace
  * `AUGM` is a boolean indicating if the measurement model is augmented
