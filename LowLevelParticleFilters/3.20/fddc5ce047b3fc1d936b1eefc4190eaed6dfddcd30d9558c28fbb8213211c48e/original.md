```
predict!(ukf::UnscentedKalmanFilter, u, p = parameters(ukf), t::Real = index(ukf) * ukf.Ts; R1 = get_mat(ukf.R1, ukf.x, u, p, t), reject, mean, cov, dynamics)
```

The prediction step for an [`UnscentedKalmanFilter`](@ref) allows the user to override, `R1` and any of the functions, reject, mean, cov, dynamics`.

# Arguments:

  * `u`: The input
  * `p`: The parameters
  * `t`: The current time
  * `R1`: The dynamics noise covariance matrix, or a function that returns the covariance matrix.
  * `reject`: A function that takes a sigma point and returns `true` if it should be rejected.
  * `mean`: The function that computes the mean of the state sigma points.
  * `cov`: The function that computes the covariance of the state sigma points.
