```
nlp = NLPModel(x, f; kwargs...)
nlp = NLPModel(x, lvar, uvar, f; kwargs...)
```

Creates a nonlinear optimization model with objective function `f`, starting point `x`, and variables bounds `lvar` and `uvar` (if provided). You can provide additional functions by keyword arguments. Here is the list of accepted function names and their signatures:

Unconstrained:

  * `grad = (gx, x) -> gx`: gradient of `f` at `x`. Stores in `gx`.
  * `objgrad = (gx, x) -> (f, gx)`: `f` and gradient of `f` at `x`. Stores in `gx`.
  * `hprod = (hv, x, v; obj_weight=1) -> ...`: Hessian at `x` times vector `v`. Stores in `hv`.
  * `hess_coord = (rows, cols, (vals, x; obj_weight=1) -> ...)`: sparse Hessian at `x` in triplet format.

Constrained:

  * `cons = ((cx, x) -> ..., lcon, ucon)`: constraints at `x`. Stores in `cx`. `lcon` and `ucon` are the constraint bounds.
  * `jprod = (jv, x, v) -> ...`: Jacobian at `x` times vector `v`. Stores in `jv`.
  * `jtprod = (jtv, x, v) -> ...`: transposed Jacobian at `x` times vector `v`. Stores in `jtv`.
  * `jac_coord = (rows, cols, (vals, x) -> ....)`: sparse Jacobian at `x` in triplet format.
  * `hprod = (hv, x, y, v; obj_weight=1) -> ...`: Lagrangian Hessian at `(x, y)` times vector `v`. Stores in `hv`.
  * `hess_coord = (rows, cols, (vals, x, y; obj_weight=1) -> ...)`: sparse Lagrangian Hessian at `(x,y)` in triplet format.
