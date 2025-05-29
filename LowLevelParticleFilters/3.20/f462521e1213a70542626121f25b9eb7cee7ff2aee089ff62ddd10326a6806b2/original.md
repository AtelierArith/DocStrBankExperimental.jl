```
correct!(ukf::UnscentedKalmanFilter{IPD, IPM, AUGD, AUGM}, u, y, p = parameters(ukf), t::Real = index(ukf) * ukf.Ts; R2 = get_mat(ukf.R2, ukf.x, u, p, t), mean, cross_cov, innovation)
```

The correction step for an [`UnscentedKalmanFilter`](@ref) allows the user to override, `R2`, `mean`, `cross_cov`, `innovation`.

# Arguments:

  * `u`: The input
  * `y`: The measurement
  * `p`: The parameters
  * `t`: The current time
  * `R2`: The measurement noise covariance matrix, or a function that returns the covariance matrix `(x,u,p,t)->R2`.
  * `mean`: The function that computes the weighted mean of the output sigma points.
  * `cross_cov`: The function that computes the weighted cross-covariance of the state and output sigma points.
  * `innovation`: The function that computes the innovation between the measured output and the predicted output.

# Extended help

To perform separate measurement updates for different sensors, see the ["Measurement models" in the documentation](@ref measurement_models)
