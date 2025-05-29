```
derivative_weight(t::RootedTree, rk::RungeKuttaMethod)
```

Compute the derivative weight (ΦᵢD)(`t`) of the [`RungeKuttaMethod`](@ref) `rk` with Butcher coefficients `A, b, c` for the rooted tree `t`.

Reference: Section 312 of

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
