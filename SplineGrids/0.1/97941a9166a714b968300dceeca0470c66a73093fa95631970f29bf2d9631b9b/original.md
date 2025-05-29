```
SplineGrid(
    spline_dimensions,
    control_points,
    weights,
    eval)
```

The SplineGrid is the central object of the `SplineGrids.jl` package, containing all information to evaluate the defined spline on the defined grid.

## Fields

  * `spline_dimensions`: A SplineDimension per dimension of the spline, containing data to evaluate basis functions.
  * `control points`: The points that define the shape of the spline, and in how many dimensions it is embedded.
  * `weights`: Control point weights to define NURBS.
  * `eval`: The array where the evaluated spline grid is stored.
