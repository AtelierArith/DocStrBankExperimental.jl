```
lyapunov(pds::ParallelDynamicalSystem, T; Ttr, Δt, d0, d0_upper, d0_lower)
```

The low-level method that is called by `lyapunov(ds::DynamicalSystem, ...)`. Use this method for looping over different initial conditions or parameters by calling [`reinit!`](@ref) to `pds`.
