```
function NodalInterpolator(FES::FESpace{T}, grid = FES.dofgrid; broken = FES.broken, component_offset = FES.coffset, kwargs...)
```

Constructs an interpolator structure that has an evaluate! function that evaluates some function at the requested nodes (items) of the grid. In broken mode only ON_CELL the items refer to cells and all nodes of these cells are evaluated.
