```
(; ll, e, S, Sᵪ, K) = correct!(kf::AbstractKalmanFilter, u, y, p = parameters(kf), t::Integer = index(kf), R2)
```

The correct step for a Kalman filter returns not only the log likelihood `ll` and the prediction error `e`, but also the covariance of the output `S`, its Cholesky factor `Sᵪ` and the Kalman gain `K`.

If `R2` stored in `kf` is a function `R2(x, u, p, t)`, this function is evaluated at the state *before* the correction is performed. The measurement noise covariance matrix `R2` stored in the filter object can optionally be overridden by passing the argument `R2`, in this case `R2` must be a matrix.

# Extended help

To perform separate measurement updates for different sensors, see the ["Measurement models" in the documentation](@ref measurement_models).
