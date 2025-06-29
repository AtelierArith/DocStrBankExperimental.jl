Fast multidimensional Chebyshev interpolation on a hypercube (Cartesian-product) domain, using a separable (tensor-product) grid of Chebyshev interpolation points.

For domain upper and lower bounds `lb` and `ub`, and a given `order` tuple, you would create an interpolator for a function `f` via:

```
using FastChebInterp
x = chebpoints(order, lb, ub) # an array of StaticVector
c = chebinterp(f.(x), lb, ub)
```

and then evaluate the interpolant for a point `y` (a vector) via `c(y)`.

We also provide a function `chebgradient(c,y)` that returns a tuple `(c(y), ∇c(y))` of the interpolant and its gradient at a point `y`.

The FastChebInterp package also supports complex and vector-valued functions `f`.  In this case, `c(y)` returns a vector of interpolants, and one can use `chebjacobian(c,y)` to compute the tuple `(c(y), J(y))` of the interpolant and its Jacobian matrix at `y`.
