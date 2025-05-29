```julia
uniform_refine(
    source_grid::ExtendableGrids.ExtendableGrid{T, K};
    store_parents
) -> ExtendableGrids.ExtendableGrid

```

generates a new ExtendableGrid by uniform refinement of each cell in the given grid

uniform refinement rules are available for these AbstractElementGeometries:

  * Line1D (bisection into two subsegments)
  * Triangle2D (red refinement into four subtriangles)
  * Quadrilateral2D (into four subquadrilaterals)
  * Tetrahedron (into eight subtetrahedrons)
  * Hexahedron (into eight subhexahedrons)

if multiple geometries are in the mesh uniform refinement will only work if all refinement rules refine faces and edges (in 3D) equally (so no hanging nodes are created)
