```
struct KalmanSmoothingSolution
```

A structure representing the solution to a Kalman smoothing problem.

# Fields

  * `sol`: A solution object containing the results of the *filtering* process.
  * `xT`: The smoothed state estimate.
  * `RT`: The smoothed state covariance.

The solution object can be plotted

```
plot(sol; plotxT=true, plotRT=true, kwargs...)
```

where

  * `plotxT`: Plot the smoothed estimates `x(t|T)`
  * `plotRT`: Plot the smoothed covariances `R(t|T)` as ribbons at ±2σ (1.96 σ to be precise)
  * The rest of the keyword arguments are the same as for [`KalmanFilteringSolution`](@ref)

When plotting a smoothing solution, the filtering solution is also plotted. The same keyword arguments as for [`KalmanFilteringSolution`](@ref) may be used to control which signals are plotted
