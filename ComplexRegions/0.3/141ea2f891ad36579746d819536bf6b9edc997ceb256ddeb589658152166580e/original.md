```
discretize(P::SimplyConnectedRegion, n=600)
```

Create an `n`×`n` grid of points on `P`. Points lying outside of `P` have a value of `NaN`.

If `P` is an exterior region, the points lie in a box a bit larger than the bounding box of `P`.

If keyword argument `limits` is specified, it must be a vector or tuple `(xmin, xmax, ymin, ymax)` specifying the limits of the grid.
