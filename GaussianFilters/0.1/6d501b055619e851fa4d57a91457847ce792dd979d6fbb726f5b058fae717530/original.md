```
measure(filter::KalmanFilter, bp::GaussianBelief, y::AbstractVector;
    u::AbstractVector = [false])
```

Uses Kalman filter to run measurement update on predicted gaussian belief bp, given measurement vector y. If u is specified and filter.o.D has been declared, then matrix D will be factored into the y predictions
