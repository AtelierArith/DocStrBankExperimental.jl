```
J = jac_nln_op!(nlp, x, Jv, Jtv)
```

Return the nonlinear Jacobian at `x` as a linear operator. The resulting object may be used as if it were a matrix, e.g., `J * v` or `J' * v`. The values `Jv` and `Jtv` are used as preallocated storage for the operations.
