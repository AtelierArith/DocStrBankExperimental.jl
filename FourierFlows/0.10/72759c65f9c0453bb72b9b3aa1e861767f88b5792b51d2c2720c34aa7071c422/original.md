```
struct ForwardEulerTimeStepper{T} <: AbstractTimeStepper{T}
```

A forward Euler timestepper for time-stepping `∂u/∂t = RHS(u, t)` via:

```julia
uⁿ⁺¹ = uⁿ + dt * RHS(uⁿ, tⁿ)
```
