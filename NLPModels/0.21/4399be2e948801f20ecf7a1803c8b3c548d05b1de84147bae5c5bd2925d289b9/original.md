```
Jtv = jtprod_lin!(nlp, rows, cols, vals, v, Jtv)
```

Evaluate $J(x)^Tv$, the linear transposed-Jacobian-vector product, where the Jacobian is given by `(rows, cols, vals)` in triplet format.
