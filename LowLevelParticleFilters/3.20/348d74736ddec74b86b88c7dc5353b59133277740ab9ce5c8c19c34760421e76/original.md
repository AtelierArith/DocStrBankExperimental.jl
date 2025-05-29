```
correct!(kf::SqKalmanFilter, u, y, p = parameters(kf), t::Real = index(kf); R2 = get_mat(kf.R2, kf.x, u, p, t))
```

For the square-root Kalman filter, a custom provided `R2` must be the upper triangular Cholesky factor of the covariance matrix of the measurement noise.
