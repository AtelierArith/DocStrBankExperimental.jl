```julia
split_grid_into(
    source_grid::ExtendableGrids.ExtendableGrid{T, K},
    targetgeometry::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> ExtendableGrids.ExtendableGrid

```

generates a new ExtendableGrid by splitting each cell into subcells of the specified targetgeometry

split rules exist for

  * Quadrilateral2D into Triangle2D
  * Hexahedron3D into Tetrahedron3D
