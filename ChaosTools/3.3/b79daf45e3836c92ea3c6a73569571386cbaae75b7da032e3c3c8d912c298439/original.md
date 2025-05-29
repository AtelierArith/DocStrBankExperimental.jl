```
lyapunovspectrum(tands::TangentDynamicalSystem, N::Int; Ttr, Δt, show_progress)
```

The low-level method that is called by `lyapunovspectrum(ds::DynamicalSystem, ...)`. Use this method for looping over different initial conditions or parameters by calling [`reinit!`](@ref) to `tands`.

Also use this method if you have a hand-coded Jacobian to pass when creating `tands`.
