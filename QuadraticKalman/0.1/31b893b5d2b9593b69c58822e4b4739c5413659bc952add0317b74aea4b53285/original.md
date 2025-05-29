```
KalmanFilterTruthPlot{T,M<:FilterOutput{<:Real}}
```

A type for plotting Kalman filter results against true states.

# Fields

  * `true_states::T`: The true state values to compare against
  * `results::M`: The output from running the Kalman filter (`FilterOutput`)

This type is used internally by the plotting recipes to create comparison plots between the true states and the Kalman filter estimates, including confidence intervals.
