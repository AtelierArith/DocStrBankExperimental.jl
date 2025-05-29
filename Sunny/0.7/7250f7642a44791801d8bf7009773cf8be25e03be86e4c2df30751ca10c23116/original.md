```
step!(sys::System, dynamics)
```

Advance the spin configuration one dynamical time-step. The `dynamics` object may be a continuous spin dynamics, such as [`Langevin`](@ref) or [`ImplicitMidpoint`](@ref), or it may be a discrete Monte Carlo sampling scheme such as [`LocalSampler`](@ref).
