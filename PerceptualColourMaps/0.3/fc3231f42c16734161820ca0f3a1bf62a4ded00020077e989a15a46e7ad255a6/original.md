pbspline - Basic Periodic B-spline

```
Usage:  S = pbspline(P, k, N)

Arguments:   P - [dim x Npts] array of control points
             k - order of spline (>= 2).
                 k = 2: Linear
                 k = 3: Quadratic, etc
             N - Optional number of points to evaluate along
                 spline. Defaults to 100.

Returns:     S - spline curve  [dim x N] spline points
```

Note that the spline points are rotated so that the first point is as close as possible to the first control point.  This is important for the formation of cyclic paths in colour space.

See also: bbspline
