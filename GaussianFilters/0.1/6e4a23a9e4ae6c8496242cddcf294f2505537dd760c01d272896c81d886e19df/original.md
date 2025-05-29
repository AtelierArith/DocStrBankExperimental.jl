```
predict(filter::ExtendedKalmanFilter, b0::GaussianBelief, u::AbstractVector)
```

Uses Extended Kalman filter to run prediction step on gaussian belief b0, given control vector u.
