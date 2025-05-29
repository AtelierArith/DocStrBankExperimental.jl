```
ImmersedBoundaryGrid(grid, ib::AbstractImmersedBoundary;
                     active_cells_map=false, active_z_columns=active_cells_map)
```

Return a grid with an `AbstractImmersedBoundary` immersed boundary (`ib`). If `active_cells_map` or `active_z_columns` are `true`, the grid will populate `interior_active_cells` and `active_z_columns` fields – a list of active indices in the interior and on a reduced x-y plane, respectively.
