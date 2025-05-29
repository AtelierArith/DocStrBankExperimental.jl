```
updatestate!(mpc::PredictiveController, u, ym, d=[]) -> x̂next
```

Call [`updatestate!`](@ref) on `mpc.estim` [`StateEstimator`](@ref).
