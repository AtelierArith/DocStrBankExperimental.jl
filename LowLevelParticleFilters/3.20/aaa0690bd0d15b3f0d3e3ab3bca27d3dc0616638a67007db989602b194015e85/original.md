```
EKFMeasurementModel{IPM}(measurement, R2, ny, Cjac, cache = nothing)
```

A measurement model for the Extended Kalman Filter.

# Arguments:

  * `IPM`: A boolean indicating if the measurement function is inplace
  * `measurement`: The measurement function `y = h(x, u, p, t)`
  * `R2`: The measurement noise covariance matrix
  * `ny`: The number of measurement variables
  * `Cjac`: The Jacobian of the measurement function `Cjac(x, u, p, t)`. If none is provided, ForwardDiff will be used.
