```
Jv = jprod!(nlp, rows, cols, vals, v, Jv)
```

Evaluate $J(x)v$, the Jacobian-vector product, where the Jacobian is given by `(rows, cols, vals)` in triplet format.
