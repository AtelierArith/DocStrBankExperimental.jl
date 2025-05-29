```
WaterfallPlot(R::MultistartResults; BiLog::Bool=true, MaxValue::Real=3000, StepTol::Real=1e-3, kwargs...)
```

Shows Waterfall plot for the given results of MultistartFit. `StepTol` is used to decide which difference of two neighbouring values in the Waterfall plot constitutes a step. `StepTol=0` deactivates step marks. `MaxValue` is used to set threshold for ignoring points whose cost function after optimization is too large compared with best optimum. `DoBiLog=false` disables logarithmic scale for cost function.
