```
smoothstepcubic(x, xedge, xwidth) -> y
```

Smoothed step function over width `xwidth` at location `xedge`.

Provides a way of smoothing a discontinuous step function so that the derivative exists, to help numerical solution methods that require a Jacobian (eg stiff ODE solvers).

Uses a cubic function in range `xedge +/- xwidth/2`, so first derivative is continuous, higher derivatives are not.

Uses [`zero_ad`](@ref) to retain AD dependency information for tracing Jacobian sparsity pattern.

Returns:

  * 0.0 for x < (xedge - xwidth/2)
  * 1.0 for x > (xedge + xwidth/2)
  * a smoothed step for xedge-xwidth/2 < x < xedge+xwidth/2
