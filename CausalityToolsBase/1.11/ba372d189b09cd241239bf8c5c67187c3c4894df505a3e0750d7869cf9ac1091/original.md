```
generate_gridpoints(axisminima, stepsizes, n_intervals_eachaxis, 
    grid::GridType = OnGrid())
```

Return a set of points forming a grid over the hyperrectangular box  spanned by

  * `(axisminima, axisminima .+ (n_intervals_eachaxis .* stepsizes)` if    `grid = OnGrid()`, and
  * `(axisminima, axisminima .+ ((n_intervals_eachaxis .+ 1) .* stepsizes)` if    `grid = OnCell()`,

where the minima along each coordinate axis (`axisminima`), the `stepsizes` along each axis, and the set of intervals (`n_intervals_per_axis`) indicating how many  equal-length intervals each axis should be divided into.

If `grid = OnGrid()`, then the bin origins are taken as the grid points.  If `grid = OnCell()`, then one additional interval is added and the grid is shifted half a bin outside the extrema along each axis, so that the grid points lie at the center of  the grid cells.
