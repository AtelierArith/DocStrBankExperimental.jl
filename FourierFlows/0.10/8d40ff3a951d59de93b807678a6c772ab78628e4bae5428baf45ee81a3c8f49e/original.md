```
struct FilteredLSRK54TimeStepper{T,V,Tf} <: AbstractTimeStepper{T}
```

A 4th-order 5-stages low-storage Runge-Kutta timestepper with spectral filtering. See [`LSRK54TimeStepper`](@ref).
