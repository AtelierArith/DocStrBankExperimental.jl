```
contour(m::Minuit, x, y; size=50, bound=2, grid=nothing, subtract_min=false)
```

Get a 2D contour of the function around the minimum.

It computes the contour via a function scan over two parameters, while keeping all other parameters fixed. The related :meth:`mncontour` works differently: for each pair of parameter values in the scan, it minimises the function with the respect to all other parameters.

This method is useful to inspect the function near the minimum to detect issues (the contours should look smooth). It is not a confidence region unless the function only has two parameters. Use :meth:`mncontour` to compute confidence regions.

## Arguments

  * `x` : First parameter for scan (name or index).
  * `y``: Second parameter for scan (name or index).
  * `size=50` : Number of scanning points per parameter (Default: 50). It can be tuple `(nx,ny)` as           the number of scanning points per parameter. Ignored if `grid` is set.
  * `bound=2` : Either ((v1min,v1max),(v2min,v2max)) or the number of `sigma`s to scan symmetrically from minimum.
  * `grid::Tuple{AbstractVector,AbstractVector} : Grid points to scan over. If`grid$is set, `size$ and `bound` are ignored.
  * `subtract_min::Bool=false` : Subtract minimum from return values

## Returns

  * Tuple(`xv`, `yv`, `zv`) : Tuple of 1D arrays with the x and y values and a 2D array with the function values.
