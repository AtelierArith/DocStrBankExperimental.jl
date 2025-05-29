```
RefinedTriangulationBinningSplitQuantile
```

A binning scheme for a triangulated simplex partition where some simplices have been  refined (subdivided by a shape-preserving simplex subdivision algorithm).

The split fraction bound controls how many times each simplex of the initial triangulation  is to be split.

## Fields

  * **`split_quantile::Float64`**: All simplices with radius larger than the    `split_quantile`-th quantile of the radii of the simplices in initial triangulation    are split with a splitting factor of `simplex_split_factor`.
  * **`simplex_split_factor::Int`**: The number of times each simplex is split.
