```julia
barycentric_refine(
    source_grid::ExtendableGrids.ExtendableGrid{T, K}
) -> ExtendableGrids.ExtendableGrid

```

は、ソースグリッド内の各セルのバリセントリック細分化によって新しいExtendableGridを生成します。

バリセントリック細分化は、以下のElementGeometriesで利用可能です。

  * Quadrilateral2D（最初にTriangle2Dに分割）
  * Triangle2D
