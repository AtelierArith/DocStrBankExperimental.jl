```
Jv = jprod_lin!(nlp, rows, cols, vals, v, Jv)
```

Evaluate $J(x)v$, the linear Jacobian-vector product, where the Jacobian is given by `(rows, cols, vals)` in triplet format.
