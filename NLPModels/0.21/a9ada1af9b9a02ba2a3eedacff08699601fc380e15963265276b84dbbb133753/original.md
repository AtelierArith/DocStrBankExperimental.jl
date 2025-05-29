```
Jtv = jtprod_nln!(nlp, rows, cols, vals, v, Jtv)
```

Evaluate $J(x)^Tv$, the nonlinear transposed-Jacobian-vector product, where the Jacobian is given by `(rows, cols, vals)` in triplet format.
