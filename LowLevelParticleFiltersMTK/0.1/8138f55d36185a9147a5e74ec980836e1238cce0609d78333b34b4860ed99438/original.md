```
propagate_distribution(f, kf, dist, args...; kwargs...)
```

Propagate a probability distribution `dist` through a nonlinear function `f` using the covariance-propagation method of filter `kf`.

## Arguments:

  * `f`: A nonlinear function `f(x, args...; kwargs...)` that takes a vector `x` and returns a vector.
  * `kf`: A state estimator, such as an `ExtendedKalmanFilter` or `UnscentedKalmanFilter`.
  * `dist`: A probability distribution, such as a `MvNormal` or `SimpleMvNormal`.
  * `args`: Additional arguments to `f`.
  * `kwargs`: Additional keyword arguments to `f`.
