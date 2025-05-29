```
kforecast(settings::KalmanSettings, X::Union{FloatVector, Nothing}, h::Int64)
```

Forecast `X` up to `h` steps ahead.

# Arguments

  * `settings`: KalmanSettings struct
  * `X`: State vector
  * `h`: Forecast horizon

    kforecast(settings::KalmanSettings, X::Union{FloatVector, Nothing}, P::Union{SymMatrix, Nothing}, h::Int64)

Forecast `X` and `P` up to `h` steps ahead.

# Arguments

  * `settings`: KalmanSettings struct
  * `X`: State vector
  * `P`: Covariance matrix of the states
  * `h`: Forecast horizon
