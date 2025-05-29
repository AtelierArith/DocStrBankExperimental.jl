```
Hv = hprod!(nlp, rows, cols, vals, v, Hv)
```

Evaluate the product of the objective or Lagrangian Hessian given by `(rows, cols, vals)` in triplet format with the vector `v` in place. Only one triangle of the Hessian should be given.
