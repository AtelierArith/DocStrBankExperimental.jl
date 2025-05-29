```
struct FilteredForwardEulerTimeStepper{T,Tf} <: AbstractTimeStepper{T}
```

A forward Euler timestepper with spectral filtering. See [`ForwardEulerTimeStepper`](@ref).
