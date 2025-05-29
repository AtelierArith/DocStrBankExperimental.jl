```
CFL(Δt [, timescale = Oceananigans.Advection.cell_advection_timescale])
```

Return an object for computing the Courant-Freidrichs-Lewy (CFL) number associated with time step `Δt` or `TimeStepWizard` and `timescale`.

See also [`AdvectiveCFL`](@ref Oceananigans.Diagnostics.AdvectiveCFL) and [`DiffusiveCFL`](Oceananigans.Diagnostics.DiffusiveCFL).
