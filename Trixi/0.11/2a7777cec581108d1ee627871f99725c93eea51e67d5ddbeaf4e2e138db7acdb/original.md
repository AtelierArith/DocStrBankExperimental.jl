```
compute_coefficients(func, t, semi::AbstractSemidiscretization)
```

Compute the discrete coefficients of the continuous function `func` at time `t` associated with the semidiscretization `semi`. For example, the discrete coefficients of `func` for a discontinuous Galerkin spectral element method ([`DGSEM`](@ref)) are the values of `func` at the Lobatto-Legendre nodes. Similarly, a classical finite difference method will use the values of `func` at the nodes of the grid assoociated with the semidiscretization `semi`.

For semidiscretizations `semi` associated with an initial condition, `func` can be omitted to use the given initial condition at time `t`.
