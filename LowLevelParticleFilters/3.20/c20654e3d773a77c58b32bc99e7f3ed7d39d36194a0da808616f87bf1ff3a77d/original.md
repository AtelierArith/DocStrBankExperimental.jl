```
predict!(kf::SqKalmanFilter, u, p = parameters(kf), t::Real = index(kf); R1 = get_mat(kf.R1, kf.x, u, p, t), α = kf.α)
```

For the square-root Kalman filter, a custom provided `R1` must be the upper triangular Cholesky factor of the covariance matrix of the process noise.
