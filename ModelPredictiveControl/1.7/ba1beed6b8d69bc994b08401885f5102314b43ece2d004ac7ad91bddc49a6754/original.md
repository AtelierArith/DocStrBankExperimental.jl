```
initstate!(mpc::PredictiveController, u, ym, d=[]) -> x̂
```

Init the states of `mpc.estim` [`StateEstimator`](@ref) and warm start `mpc.Z̃` at zero.

It also stores `u - mpc.estim.model.uop` at `mpc.lastu0` for converting the input increments $\mathbf{ΔU}$ to inputs $\mathbf{U}$.
