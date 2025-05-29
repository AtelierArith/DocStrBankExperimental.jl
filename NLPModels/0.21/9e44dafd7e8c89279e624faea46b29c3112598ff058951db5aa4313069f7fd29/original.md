```
Jtv = jtprod!(nlp, rows, cols, vals, v, Jtv)
```

Evaluate $J(x)^Tv$, the transposed-Jacobian-vector product, where the Jacobian is given by `(rows, cols, vals)` in triplet format.
