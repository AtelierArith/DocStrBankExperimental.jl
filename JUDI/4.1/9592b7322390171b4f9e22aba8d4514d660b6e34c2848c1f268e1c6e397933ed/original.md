```
setup_3D_grid(x, y, z)
```

Converts one dimensional input (x, y, z) into three dimensional coordinates. The number of point created is `length(x)*lenght(y)` with all the x/y pairs and each pair at depth z[idx[x]]. `x` and `z` must have the same size.

Parameters:

  * `x`: X coordinates.
  * `y`: Y coordinates.
  * `z`: Z coordinates.
