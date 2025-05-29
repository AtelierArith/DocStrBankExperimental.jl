```
ContQuadGKJL(; order = 7, norm = norm, rho = 1.0, rootmeth = IteratedIntegration.ContQuadGK.NewtonDeflation())
```

A 1d contour deformation quadrature scheme for scalar, complex-valued integrands. It defaults to regular `quadgk` behavior on the real axis, but if it finds a root of 1/f nearby, in the sense of Bernstein ellipse for the standard segment `[-1,1]` with semiaxes `cosh(rho)` and `sinh(rho)`, on either the upper/lower half planes, then it dents the contour away from the presumable pole.
