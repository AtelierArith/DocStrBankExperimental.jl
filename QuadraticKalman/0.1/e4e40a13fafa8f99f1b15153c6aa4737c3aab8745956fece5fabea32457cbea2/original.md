```
KalmanSmootherTruthPlot{T,M<:SmootherOutput{<:Real}}
```

A type for plotting Kalman smoother results against true states.

# Fields

  * `true_states::T`: An `N×T_bar` matrix representing the actual underlying state values, `X_t`, that the model is attempting to filter. Each column corresponds to the state at a specific time step.
  * `results::M`: The output from running the Kalman smoother, provided as a `SmootherOutput`, which includes the smoothed state estimates and associated covariance matrices.

This type is used internally by the plotting recipes to create comparison plots between the true states and the Kalman smoother estimates. The plots typically display:

  * The true state trajectories (as represented by the `N×T_bar` matrix of `X_t` values).
  * The smoother’s state estimates along with confidence intervals,

thus facilitating a visual diagnostic of the smoother's performance in recovering the true state dynamics.
