```
sol = smooth(filtersol)
sol = smooth(kf::AbstractKalmanFilter, u::Vector, y::Vector, p=parameters(kf))
```

Returns a [`KalmanSmoothingSolution`](@ref) with smoothed estimates of state `xT` and covariance `RT` given all input output data `u,y` or an existing filtering solution `filtersol` obtained from [`forward_trajectory`](@ref).

The return smoothing can be plotted using `plot(sol)`, see [`KalmanSmoothingSolution`](@ref) and [`KalmanFilteringSolution`](@ref) for details.
