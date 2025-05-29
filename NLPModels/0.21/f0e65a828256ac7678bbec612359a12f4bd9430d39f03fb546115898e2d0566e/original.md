```
J = jac_op!(nlp, rows, cols, vals, Jv, Jtv)
```

Return the Jacobian given by `(rows, cols, vals)` as a linear operator. The resulting object may be used as if it were a matrix, e.g., `J * v` or `J' * v`. The values `Jv` and `Jtv` are used as preallocated storage for the operations.
