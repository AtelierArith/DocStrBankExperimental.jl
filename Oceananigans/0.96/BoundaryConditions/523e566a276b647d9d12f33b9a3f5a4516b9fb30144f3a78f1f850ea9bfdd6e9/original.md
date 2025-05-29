```
FieldBoundaryConditions(grid, location, indices=(:, :, :);
                        west     = default_auxiliary_bc(grid, boundary, loc),
                        east     = default_auxiliary_bc(grid, boundary, loc),
                        south    = default_auxiliary_bc(grid, boundary, loc), 
                        north    = default_auxiliary_bc(grid, boundary, loc), 
                        bottom   = default_auxiliary_bc(grid, boundary, loc), 
                        top      = default_auxiliary_bc(grid, boundary, loc), 
                        immersed = NoFluxBoundaryCondition())
```

Return boundary conditions for auxiliary fields (fields whose values are derived from a model's prognostic fields) on `grid` and at `location`.

# Keyword arguments

Keyword arguments specify boundary conditions on the 6 possible boundaries:

  * `west`, left end point in the `x`-direction where `i = 1`
  * `east`, right end point in the `x`-direction where `i = grid.Nx`
  * `south`, left end point in the `y`-direction where `j = 1`
  * `north`, right end point in the `y`-direction where `j = grid.Ny`
  * `bottom`, right end point in the `z`-direction where `k = 1`
  * `top`, right end point in the `z`-direction where `k = grid.Nz`
  * `immersed`: boundary between solid and fluid for immersed boundaries

If a boundary condition is unspecified, the default for auxiliary fields and the topology in the boundary-normal direction is used:

  * `PeriodicBoundaryCondition` for `Periodic` directions
  * `GradientBoundaryCondition(0)` for `Bounded` directions and `Centered`-located fields
  * `nothing` for `Bounded` directions and `Face`-located fields
  * `nothing` for `Flat` directions and/or `Nothing`-located fields
