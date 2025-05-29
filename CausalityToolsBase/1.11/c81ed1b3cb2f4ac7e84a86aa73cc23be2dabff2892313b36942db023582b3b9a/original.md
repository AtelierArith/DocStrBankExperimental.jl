```
generate_gridpoints(points, binning_scheme::RectangularBinning, 
    grid::GridType = OnGrid())
```

Return a set of points forming a rectangular grid covering a  hyperrectangular box specified  by the `binning_scheme` and `grid` type.  Provided a suitable binning scheme is given, this grid will provide a  covering of `points`. See the documentation for `RectangularBinning` for  more details. 

## Arguments

  * **`points`**: A vector of points or a `Dataset` instance.
  * **`binning_scheme`**: A `RectangularBinning` instance.
  * **`grid`**: A `GridType` instance. The grid follows the same convention    as in Interpolations.jl. Valid choices are `OnGrid()` (uses the bin    origins as the grid points), and `OnCell()`, which adds an additional    interval along each axis, shifts the grid half a bin outside the    extrema along each axis and retursn the centers of the resulting    grid cells.

## Examples

For example,

```julia
using CausalityToolsBase, DelayEmbeddings

pts = Dataset([rand(3) for i = 1:100])
generate_gridpoints(pts, RectangularBinning(10), OnGrid()
```

generates a rectangular grid covering the range of `pts` constructed  by subdividing each coordinate axis into 10 equal-length intervals. 

For example,

```julia
using CausalityToolsBase, DelayEmbeddings

pts = Dataset([rand(3) for i = 1:100])
generate_gridpoints(pts, RectangularBinning(10), OnCell()
```

will do the same, but adds another interval (11 in total), shifts the  entire hypercube so that the minima and maxima along each axis lie  half a bin outside the original extrema, then returns the centers of  the grid cells.
