```
aggregation(mg::Microgrid, oper_traj::OperationTraj, smoothing::Smoothing=NoSmoothing)
```

Aggregate operation time series `oper_traj` into yearly statistics for the the microgrid `mg` (returned as an `OperationStats` object).

Discontinuous computations can optionally be smoothed (relaxed) using the `Smoothing` parameters `transition` and `gain` (see their doc). Smoothing is recommended when using gradient-based optimization.
