```
vals = jac_lin_coord!(nlp, x, vals)
```

Evaluate $J(x)$, the linear constraints Jacobian at `x` in sparse coordinate format, overwriting `vals`.
