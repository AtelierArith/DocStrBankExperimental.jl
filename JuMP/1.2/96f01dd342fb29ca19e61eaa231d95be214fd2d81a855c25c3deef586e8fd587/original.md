```
barrier_iterations(model::Model)
```

Gets the cumulative number of barrier iterations during the most recent optimization.

Solvers must implement `MOI.BarrierIterations()` to use this function.
