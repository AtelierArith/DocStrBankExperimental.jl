```julia
uniform_refine(
    source_grid::ExtendableGrids.ExtendableGrid{T, K};
    store_parents
) -> ExtendableGrids.ExtendableGrid

```

は、与えられたグリッド内の各セルを均一に細分化することによって新しい ExtendableGrid を生成します。

均一細分化ルールは、これらの AbstractElementGeometries に対して利用可能です：

  * Line1D（2つのサブセグメントへの二分割）
  * Triangle2D（4つのサブ三角形への赤細分化）
  * Quadrilateral2D（4つのサブ四角形への細分化）
  * Tetrahedron（8つのサブテトラヘドロンへの細分化）
  * Hexahedron（8つのサブヘキサヘドロンへの細分化）

メッシュに複数のジオメトリがある場合、均一細分化はすべての細分化ルールが面とエッジ（3D）を同等に細分化する場合にのみ機能します（したがって、ハンギングノードは作成されません）。
