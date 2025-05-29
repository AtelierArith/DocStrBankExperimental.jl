```
simulate(mg::Microgrid, smoothing::Smoothing=NoSmoothing)
```

Simulate the technical and economic performance of a Microgrid `mg`.

Discontinuous computations can optionally be smoothed (relaxed) using the `Smoothing` parameters `transition` and `gain` (see their doc). Smoothing is recommended when using gradient-based optimization.

Returns:

  * Operational trajectories from `sim_operation` (should be optional in future version)
  * Operational statistics from `sim_operation`
  * Microgrid project costs from `sim_economics`
