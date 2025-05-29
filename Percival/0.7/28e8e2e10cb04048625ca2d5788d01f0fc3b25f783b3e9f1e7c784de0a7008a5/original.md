```
AugLagModel(model, y, μ, x, fx, cx)
```

Given a model

$$
\min \ f(x) \quad s.t. \quad c(x) = 0, \quad l ≤ x ≤ u,
$$

this new model represents the subproblem of the augmented Lagrangian method

$$
\min \ f(x) - yᵀc(x) + \tfrac{1}{2} μ \|c(x)\|^2 \quad s.t. \quad l ≤ x ≤ u,
$$

where y is an estimates of the Lagrange multiplier vector and μ is the penalty parameter.

In addition to keeping `meta` and `counters` as any NLPModel, an AugLagModel also stores

  * `model`: The internal model defining $f$, $c$ and the bounds,
  * `y`: The multipliers estimate,
  * `μ`: The penalty parameter,
  * `x`: Reference to the last point at which the function `c(x)` was computed,
  * `fx`: Reference to `f(x)`,
  * `cx`: Reference to `c(x)`,
  * `μc_y`: storage for y - μ * cx,
  * `store_Jv` and `store_JtJv`: storage used in `hprod!`.

Use the functions `update_cx!`, `update_y!` and `update_μ!` to update these values.
