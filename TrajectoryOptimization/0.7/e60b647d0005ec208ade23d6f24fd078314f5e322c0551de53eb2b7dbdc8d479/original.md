```
QuadraticCost{n,m,T,TQ,TR}
```

Cost function of the form

$$
\frac{1}{2} x^T Q x + \frac{1}{2} u^T R u + u^T H x + q^T x + r^T u + c
$$

where $R$ must be positive definite, $Q$ and $Q_f$ must be positive semidefinite.

The type parameters `TQ` and `TR` specify the type of $Q$ and $R$.

# Constructor

```
QuadraticCost(Q, R, H, q, r, c; kwargs...)
QuadraticCost(Q, R; H, q, r, c, kwargs...)
```

Any optional or omitted values will be set to zero(s). The keyword arguments are

  * `terminal` - A `Bool` specifying if the cost function is terminal cost or not.
  * `checks` - A `Bool` specifying if `Q` and `R` will be checked for the required definiteness.
