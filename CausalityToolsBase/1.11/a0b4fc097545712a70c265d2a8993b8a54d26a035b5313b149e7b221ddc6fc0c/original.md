```
RefinedTriangulationBinningMaxRadius
```

A binning scheme for a triangulated simplex partition where some simplices have been  refined (subdivided by a shape-preserving simplex subdivision algorithm).

The maximum radius bound is applied by first doing an initial triangulation, the  splitting simplices whose radius is large until all simplices have radii less than  the resulting radius bound.

## Fields

  * **`max_radius_frac::Float64`**: The maximum radius expressed as a fraction of the

radius of the largest simplex of the initial triangulation.
