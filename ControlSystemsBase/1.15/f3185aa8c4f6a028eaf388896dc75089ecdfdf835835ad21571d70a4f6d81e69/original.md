```
U = grampd(sys, opt; kwargs...)
```

Return a Cholesky factor `U` of the grammian of system `sys`. If `opt` is `:c`, computes the controllability grammian `G = U*U'`. If `opt` is `:o`, computes the observability grammian `G = U'U`.

Obtain a `Cholesky` object by `Cholesky(U)` for observability grammian

Uses `MatrixEquations.plyapc/plyapd`. For keyword arguments, see the docstring of `ControlSystemsBase.MatrixEquations.plyapc/plyapd`
