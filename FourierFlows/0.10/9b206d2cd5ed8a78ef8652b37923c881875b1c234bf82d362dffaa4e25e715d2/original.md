```
struct RK4TimeStepper{T} <: AbstractTimeStepper{T}
```

A 4th-order Runge-Kutta timestepper for time-stepping `∂u/∂t = RHS(u, t)` via:

```julia
uⁿ⁺¹ = uⁿ + dt/6 * (k₁ + 2 * k₂ + 2 * k₃ + k₄)
```

where

```julia
k₁ = RHS(uⁿ, tⁿ)
k₂ = RHS(uⁿ + k₁ * dt/2, tⁿ + dt/2)
k₃ = RHS(uⁿ + k₂ * dt/2, tⁿ + dt/2)
k₄ = RHS(uⁿ + k₃ * dt, tⁿ + dt)
```

!!! info "Usage"
    If your simulation is limited by memory then consider switching to [`LSRK54TimeStepper`](@ref). The [`LSRK54TimeStepper`](@ref) timestepper has about half the memory footprint compared to the `RK4TimeStepper` with a about 25%-30% performance trade off.

