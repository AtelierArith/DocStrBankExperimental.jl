```
FieldBoundaryConditions(; kwargs...)
```

Return a template for boundary conditions on prognostic fields.

# Keyword arguments

Keyword arguments specify boundary conditions on the 7 possible boundaries:

  * `west`: left end point in the `x`-direction where `i = 1`
  * `east`: right end point in the `x`-direction where `i = grid.Nx`
  * `south`: left end point in the `y`-direction where `j = 1`
  * `north`: right end point in the `y`-direction where `j = grid.Ny`
  * `bottom`: right end point in the `z`-direction where `k = 1`
  * `top`: right end point in the `z`-direction where `k = grid.Nz`
  * `immersed`: boundary between solid and fluid for immersed boundaries

If a boundary condition is unspecified, the default for prognostic fields and the topology in the boundary-normal direction is used:

  * `PeriodicBoundaryCondition` for `Periodic` directions
  * `NoFluxBoundaryCondition` for `Bounded` directions and `Centered`-located fields
  * `ImpenetrableBoundaryCondition` for `Bounded` directions and `Face`-located fields
  * `nothing` for `Flat` directions and/or `Nothing`-located fields
