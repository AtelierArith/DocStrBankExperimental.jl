```julia
split_grid_into(
    source_grid::ExtendableGrids.ExtendableGrid{T, K},
    targetgeometry::Type{<:ExtendableGrids.AbstractElementGeometry}
) -> ExtendableGrids.ExtendableGrid

```

指定されたtargetgeometryのサブセルに各セルを分割することによって新しいExtendableGridを生成します。

分割ルールは次の通りです。

  * Quadrilateral2DをTriangle2Dに
  * Hexahedron3DをTetrahedron3Dに
