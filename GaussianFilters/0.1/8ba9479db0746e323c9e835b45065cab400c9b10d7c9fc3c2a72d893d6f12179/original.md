```
predict(filter::UnscentedKalmanFilter, b0::GaussianBelief, u::AbstractVector)
```

Uses Unscented Kalman filter to run prediction step on gaussian belief b0, given control vector u.
