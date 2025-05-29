```
KalmanFilteringSolution{Tx,Txt,TR,TRt,Tll} <: AbstractFilteringSolution
```

# Fields

  * `x`: predictions $x(t+1|t)$ (plotted if `plotx=true`)
  * `xt`: filtered estimates $x(t|t)$ (plotted if `plotxt=true`)
  * `R`: predicted covariance matrices $R(t+1|t)$ (plotted if `plotR=true`)
  * `Rt`: filter covariances $R(t|t)$ (plotted if `plotRt=true`)
  * `ll`: loglikelihood
  * `e`: prediction errors $e(t|t-1) = y - ŷ(t|t-1)$ (plotted if `plote=true`)

# Plot

The solution object can be plotted

```
plot(sol, plotx=true, plotxt=true, plotR=true, plotRt=true, plote=true, plotu=true, ploty=true, plotyh=true, plotyht=true, name="")
```

where

  * `plotx`: Plot the predictions `x(t|t-1)`
  * `plotxt`: Plot the filtered estimates `x(t|t)`
  * `plotR`: Plot the predicted covariances `R(t|t-1)` as ribbons at ±2σ (1.96 σ to be precise)
  * `plotRt`: Plot the filter covariances `R(t|t)` as ribbons at ±2σ (1.96 σ to be precise)
  * `plote`: Plot the prediction errors `e(t|t-1) = y - ŷ(t|t-1)`
  * `plotu`: Plot the input
  * `ploty`: Plot the measurements
  * `plotyh`: Plot the predicted measurements `ŷ(t|t-1)`
  * `plotyht`: Plot the filtered measurements `ŷ(t|t)`
  * `name`: a string that is prepended to the labels of the plots, which is useful when plotting multiple solutions in the same plot.

To modify the signal names used in legend entries, construct an instance of [`SignalNames`](@ref) and pass this to the filter (or directly to the plot command) using the `names` keyword argument.
