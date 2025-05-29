```
residual_order_condition(t::RootedTree, rk::RungeKuttaMethod)
```

The residual of the order condition   `(Φ(t) - 1/γ(t)) / σ(t)` with [`elementary_weight`](@ref) `Φ(t)`, [`density`](@ref) `γ(t)`, and [`symmetry`](@ref) `σ(t)` of the [`RungeKuttaMethod`](@ref) `rk` with Butcher coefficients `A, b, c` for the rooted tree `t`.

Reference: Section 315 of

  * Butcher, John Charles. Numerical methods for ordinary differential equations. John Wiley & Sons, 2008.
