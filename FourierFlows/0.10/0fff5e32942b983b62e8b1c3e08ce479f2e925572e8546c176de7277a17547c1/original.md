```
struct FilteredRK4TimeStepper{T,Tf} <: AbstractTimeStepper{T}
```

A 4th-order Runge-Kutta timestepper with spectral filtering. See [`RK4TimeStepper`](@ref).
