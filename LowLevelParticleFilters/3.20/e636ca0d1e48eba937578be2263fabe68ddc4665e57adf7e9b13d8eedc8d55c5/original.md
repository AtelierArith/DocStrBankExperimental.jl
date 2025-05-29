```
UKFMeasurementModel{inplace_measurement,augmented_measurement}(measurement, R2, ny, ne, innovation, mean, cov, cross_cov, weight_params, cache = nothing)
```

A measurement model for the Unscented Kalman Filter.

# Arguments:

  * `measurement`: The measurement function `y = h(x, u, p, t)`
  * `R2`: The measurement noise covariance matrix
  * `ny`: The number of measurement variables
  * `ne`: If `augmented_measurement` is `true`, the number of measurement noise variables
  * `innovation(y::AbstractVector, yh::AbstractVector)` where the arguments represent (measured output, predicted output)
  * `mean(ys::AbstractVector{<:AbstractVector})`: computes the mean of the vector of vectors of output sigma points.
  * `cov(ys::AbstractVector{<:AbstractVector}, y::AbstractVector)`: computes the covariance matrix of the output sigma points.
  * `cross_cov(xs::AbstractVector{<:AbstractVector}, x::AbstractVector, ys::AbstractVector{<:AbstractVector}, y::AbstractVector, W::UKFWeights)` where the arguments represents (state sigma points, mean state, output sigma points, mean output, weights). The function should return the weighted **cross-covariance** matrix between the state and output sigma points.
  * `weight_params`: A type that holds the parameters for the unscented-transform weights. See [`UnscentedKalmanFilter`](@ref) and [Docs: Unscented transform](https://baggepinnen.github.io/LowLevelParticleFilters.jl/dev/ut/) for more information.
