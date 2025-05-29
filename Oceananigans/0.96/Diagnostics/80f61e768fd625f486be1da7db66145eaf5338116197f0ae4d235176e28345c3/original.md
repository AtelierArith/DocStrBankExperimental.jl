```
AdvectiveCFL(Δt)
```

Return an object for computing the Courant-Freidrichs-Lewy (CFL) number associated with time step `Δt` or `TimeStepWizard` and the time scale for advection across a cell. The advective CFL is, e.g., $U Δt / Δx$.

# Example

```jldoctest
julia> using Oceananigans

julia> model = NonhydrostaticModel(grid = RectilinearGrid(size=(16, 16, 16), extent=(8, 8, 8)));

julia> Δt = 1.0;

julia> cfl = AdvectiveCFL(Δt);

julia> model.velocities.u .= π;

julia> cfl(model)
6.283185307179586
```
