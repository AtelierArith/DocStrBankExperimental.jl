```julia
barycentric_refine(
    source_grid::ExtendableGrids.ExtendableGrid{T, K}
) -> ExtendableGrids.ExtendableGrid

```

generates a new ExtendableGrid by barycentric refinement of each cell in the source grid

barycentric refinement is available for these ElementGeometries

  * Quadrilateral2D (first split into Triangle2D)
  * Triangle2D
