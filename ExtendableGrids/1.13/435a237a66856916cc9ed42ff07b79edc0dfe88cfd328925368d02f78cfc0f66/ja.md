```julia
split_grid_into(
    source_grid::ExtendableGrids.ExtendableGrid{T, K},
    targetgeometry::Type{<:ExtendableGrids.AbstractElementGeometry};
    store_parents
) -> ExtendableGrids.ExtendableGrid

```

は、指定された targetgeometry のサブセルに各セルを分割することによって新しい ExtendableGrid を生成します。

分割ルールは次の通りです。

  * Quadrilateral2D を Triangle2D に
  * Hexahedron3D を Tetrahedron3D に
