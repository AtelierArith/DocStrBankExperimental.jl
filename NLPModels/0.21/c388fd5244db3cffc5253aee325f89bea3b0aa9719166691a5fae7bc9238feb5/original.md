```
vals = jac_nln_coord!(nlp, x, vals)
```

Evaluate $J(x)$, the nonlinear constraints Jacobian at `x` in sparse coordinate format, overwriting `vals`.
