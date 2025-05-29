bbspline - Basic B-spline

```
Usage:  S = bbspline(P, k, N)

Arguments:   P - [dim x Npts] array of control points
             k - order of spline (>= 2).
                 k = 2: Linear
                 k = 3: Quadratic, etc
             N - Optional number of points to evaluate along
                 spline. Defaults to 100.

Returns:     S - spline curve  [dim x N] spline points
```

See also: pbspline
