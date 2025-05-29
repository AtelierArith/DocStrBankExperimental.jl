```
struct LSRK54TimeStepper{T} <: AbstractTimeStepper{T}
```

A 4th-order 5-stages 2-storage Runge-Kutta timestepper for time-stepping `∂u/∂t = RHS(u, t)` via:

```julia
S² = 0

for i = 1:5
  S² = Aᵢ * S² + dt * RHS(uⁿ, t₀ + Cᵢ * dt)
  uⁿ += Bᵢ * S²
end

uⁿ⁺¹ = uⁿ
```

where `Aᵢ`, `Bᵢ`, and `Cᵢ` are the $A$, $B$, and $C$ coefficients from the LSRK table at the $i$-th stage. For details, refer to [Carpenter-Kennedy-1994](@citet).

!!! info "Usage"
    The `LSRK54TimeStepper` is *slower* than the [`RK4TimeStepper`](@ref) but has *less* memory footprint; half compared to [`RK4TimeStepper`](@ref).

    If your simulation is bound by performance then use [`RK4TimeStepper`](@ref); if your simulation is bound by memory then consider using `LSRK54TimeStepper`.

