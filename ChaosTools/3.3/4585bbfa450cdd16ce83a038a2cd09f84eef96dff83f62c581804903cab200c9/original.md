```
gali(tands::TangentDynamicalSystem, T; threshold = 1e-12, Δt = 1)
```

The low-level method that is called by `gali(ds::DynamicalSystem, ...)`. Use this method for looping over different initial conditions or parameters by calling [`reinit!`](@ref) to `tands`.

The order of $\text{GALI}_k$ computed is the amount of deviation vectors in `tands`.

Also use this method if you have a hand-coded Jacobian to pass when creating `tands`.
