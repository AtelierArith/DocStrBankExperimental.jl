```
BSpline(t[; k′=3])
```

Create the B-spline basis corresponding to the knot set `t`. `k′` is the highest polynomial order of operators for which it should be possible to compute the matrix elements exactly (via Gauß–Legendre quadrature). The default `k′=3` corresponds to operators O(x²).
