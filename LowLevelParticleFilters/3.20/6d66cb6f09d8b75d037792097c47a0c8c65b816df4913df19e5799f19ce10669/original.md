```
predict!(kf::AbstractKalmanFilter, u, p = parameters(kf), t::Integer = index(kf); R1, α = kf.α)
```

Perform the prediction step (updating the state estimate to $x(t+1|t)$). If `R1` stored in `kf` is a function `R1(x, u, p, t)`, this function is evaluated at the state *before* the prediction is performed. The dynamics noise covariance matrix `R1` stored in `kf` can optionally be overridden by passing the argument `R1`, in this case `R1` must be a matrix.
