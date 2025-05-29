```
struct AB3TimeStepper{T} <: AbstractTimeStepper{T}
```

A 3rd-order Adams-Bashforth timestepper for time-stepping `∂u/∂t = RHS(u, t)` via:

```julia
uⁿ⁺¹ = uⁿ + dt/12 * (23 * RHS(uⁿ, tⁿ) - 16 * RHS(uⁿ⁻¹, tⁿ⁻¹) + 5 * RHS(uⁿ⁻², tⁿ⁻²))
```

Adams-Bashforth is a multistep method, i.e., it not only requires information from the `n`-th time-step (`uⁿ`) but also from the previous two timesteps (`uⁿ⁻¹` and `uⁿ⁻²`). For the first two timesteps, it falls back to a forward Euler timestepping scheme:

```julia
uⁿ⁺¹ = uⁿ + dt * RHS(uⁿ, tⁿ)
```
