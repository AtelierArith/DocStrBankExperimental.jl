```
sol = forward_trajectory(kf::AbstractKalmanFilter, u::Vector, y::Vector, p=parameters(kf); debug=false)
```

Run a Kalman filter forward to perform (offline / batch) filtering along an entire trajectory `u, y`.

Returns a KalmanFilteringSolution: with the following

  * `x`: predictions $x(t|t-1)$
  * `xt`: filtered estimates $x(t|t)$
  * `R`: predicted covariance matrices $R(t|t-1)$
  * `Rt`: filter covariances $R(t|t)$
  * `ll`: loglik

`sol` can be plotted

```
plot(sol::KalmanFilteringSolution; plotx = true, plotxt=true, plotu=true, ploty=true)
```

See [`KalmanFilteringSolution`](@ref) for more details.

# Extended help

## Very large systems

If your system is very large, i.e., the dimension of the state is very large, and the arrays `u,y` are long, this function may use a lot of memory to store all covariance matrices `R, Rt`. If you do not need all the information retained by this function, you may opt to call one of the functions

  * [`loglik`](@ref)
  * [`LowLevelParticleFilters.sse`](@ref)
  * [`LowLevelParticleFilters.prediction_errors!`](@ref)

That store significantly less information. The amount of computation performed by all of these functions is identical, the only difference lies in what is stored and returned.

## Callbacks

For advanced usage, such as implementing conditional resetting and adaptive covariance, one may make use of the callback functions

  * `pre_correct_cb(kf, u, y, p, t)`: called before the correction step, returns either `nothing` or a covariance matrix `R2` to use in the correction step.
  * `pre_predict_cb(kf, u, y, p, t, ll, e, S, Sᵪ)`: called before the prediction step, returns either `nothing` or a covariance matrix `R1` to use in the prediction step. The arguments to this callback are `filter, input, measurement, parameters, time, loglikelihood, prediction error, innovation covariance and Cholesky factor of the innovation covariance`, essentially all the information available after the correct step.

The filter loop consists of the following steps, in this order:

1. `pre_correct_cb`
2. `correct!`
3. `pre_predict_cb`
4. `predict!`
