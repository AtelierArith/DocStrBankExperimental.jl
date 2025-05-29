```
MeroQuadGKJL(; order = 7, norm = norm, rho = 1.0, rootmeth = IteratedIntegration.MeroQuadGK.NewtonDeflation())
```

A 1d pole subtraction quadrature scheme for scalar, complex-valued integrands that are meromorphic. It defaults to regular `quadgk` behavior on the real axis, but if it finds nearby roots of 1/f, in the sense of Bernstein ellipse for the standard segment `[-1,1]` with semiaxes `cosh(rho)` and `sinh(rho)`, it attempts pole subtraction on that segment.
