```
elementary_weight(t::RootedTree, rk::RungeKuttaMethod)
elementary_weight(t::RootedTree, A::AbstractMatrix, b::AbstractVector, c::AbstractVector)
```

Compute the elementary weight Φ(`t`) of the [`RungeKuttaMethod`](@ref) `rk` with Butcher coefficients `A, b, c` for a rooted tree `t``.

Reference: Section 312 of

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
