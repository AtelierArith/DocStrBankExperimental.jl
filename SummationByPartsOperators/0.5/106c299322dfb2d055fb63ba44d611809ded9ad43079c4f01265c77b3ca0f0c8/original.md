```
integrate_boundary([func = identity,] u, D::AbstractDerivativeOperator)
```

Map the function `func` to the coefficients `u` and integrate along the boundary. For classical 1D operators this is `func(u[end]) - func(u[begin])`. For periodic 1D operators this is zero.
