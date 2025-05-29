```
overlap(poly::PiecewiseLegendrePoly, f; 
    rtol=eps(T), return_error=false, maxevals=10^4, points=T[])
```

Evaluate overlap integral of `poly` with arbitrary function `f`.

Given the function `f`, evaluate the integral

```
∫ dx f(x) poly(x)
```

using adaptive Gauss-Legendre quadrature.

`points` is a sequence of break points in the integration interval where local difficulties of the integrand may occur (e.g. singularities, discontinuities).
