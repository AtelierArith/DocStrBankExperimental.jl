```
DiagonalCost{n,m,T}
```

Cost function of the form

$$
\frac{1}{2} x^T Q x + \frac{1}{2} u^T R u + q^T x + r^T u + c
$$

where $Q$ and $R$ are positive semi-definite and positive definite diagonal matrices, respectively, and $x$ is `n`-dimensional and $u$ is `m`-dimensional.

# Constructors

```
DiagonalCost(Qd, Rd, q, r, c; kwargs...)
DiagonalCost(Q, R, q, r, c; kwargs...)
DiagonalCost(Qd, Rd; [q, r, c, kwargs...])
DiagonalCost(Q, R; [q, r, c, kwargs...])
```

where `Qd` and `Rd` are the diagonal vectors, and `Q` and `R` are matrices.

Any optional or omitted values will be set to zero(s). The keyword arguments are

  * `terminal` - A `Bool` specifying if the cost function is terminal cost or not.
  * `checks` - A `Bool` specifying if `Q` and `R` will be checked for the required definiteness.
