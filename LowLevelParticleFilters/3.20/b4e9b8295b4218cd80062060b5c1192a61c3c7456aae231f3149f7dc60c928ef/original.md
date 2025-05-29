```
IEKFMeasurementModel{T,IPM}(measurement::M, R2; nx, ny, Cjac = nothing, step = 1.0, maxiters = 10, epsilon = 1e-8)
```

  * `T` is the element type used for arrays
  * `IPM` is a boolean indicating if the measurement function is inplace
