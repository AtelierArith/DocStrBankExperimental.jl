```
SizedKalmanStatus(R::SymMatrix, T::Int64)
SizedKalmanStatus(R::UniformScaling{Float64}, T::Int64)
SizedKalmanStatus(settings::KalmanSettings)
```

Return an initialised `SizedKalmanStatus` struct. `R` specialises the struct for the regular / sequential implementation of the Kalman filter and smoother.
