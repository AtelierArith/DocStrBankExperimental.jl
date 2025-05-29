```
IEKFMeasurementModel{IPM}(measurement, R2, ny, Cjac, cache = nothing)
```

A measurement model for the Iterated Extended Kalman Filter.

# Arguments:

  * `IPM`: A boolean indicating if the measurement function is inplace
  * `measurement`: The measurement function `y = h(x, u, p, t)`
  * `R2`: The measurement noise covariance matrix
  * `ny`: The number of measurement variables
  * `Cjac`: The Jacobian of the measurement function `Cjac(x, u, p, t)`. If none is provided, ForwardDiff will be used.
  * `step`: The step size in the Gauss-Newton method. Should be Float64 between 0 and 1.
  * `maxiters`: The maximum number of iterations of the Gauss-Newton method inside the IEKF
  * `epsilon`: The convergence criterion for the Gauss-Newton method inside the IEKF
  * `cache`: A cache for the Jacobian
