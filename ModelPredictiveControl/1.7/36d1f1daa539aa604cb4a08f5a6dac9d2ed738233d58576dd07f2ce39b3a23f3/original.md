```
setstate!(estim::StateEstimator, x̂[, P̂]) -> estim
```

Set `estim.x̂0` to `x̂ - estim.x̂op` from the argument `x̂`, and `estim.P̂` to `P̂` if applicable. 

The covariance error estimate `P̂` can be set only if `estim` is a [`StateEstimator`](@ref) that computes it.
