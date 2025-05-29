```
PredictionStateSpace{T, ST <: AbstractStateSpace{T}, KT, QT, RT, ST2} <: AbstractPredictionStateSpace{T}
PredictionStateSpace(sys, K, Q=nothing, R=nothing, S=nothing)
```

A statespace type that contains an additional Kalman-filter model for prediction purposes.

# Arguments:

  * `sys`: DESCRIPTION
  * `K`: Infinite-horizon Kalman gain
  * `Q = nothing`: Dynamics covariance
  * `R = nothing`: Measurement covariance
  * `S = nothing`: Cross-covariance
