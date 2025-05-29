```
predict(filter::KalmanFilter, b0::GaussianBelief, u::AbstractVector)
```

Uses Kalman filter to run prediction step on gaussian belief b0, given control vector u.
