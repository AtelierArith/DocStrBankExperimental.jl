```
initstate!(mpc::PredictiveController, u, ym, d=[]) -> x̂
```

Init the states of `mpc.estim` [`StateEstimator`](@ref) and warm start `mpc.Z̃` at zero.
