```
chebinterp(vals, lb, ub; tol=eps)
```

Given a multidimensional array `vals` of function values (at points corresponding to the coordinates returned by `chebpoints`), and arrays `lb` and `ub` of the lower and upper coordinate bounds of the domain in each direction, returns a Chebyshev interpolation object (a `ChebPoly`).

This object `c = chebinterp(vals, lb, ub)` can be used to evaluate the interpolating polynomial at a point `x` via `c(x)`.

The elements of `vals` can be vectors as well as numbers, in order to interpolate vector-valued functions (i.e. to interpolate several functions at once).

The `tol` argument specifies a relative tolerance below which Chebyshev coefficients are dropped; it defaults to machine precision for the precision of `float(vals)`.   Passing `tol=0` will keep all coefficients up to the order passed to `chebpoints`.
