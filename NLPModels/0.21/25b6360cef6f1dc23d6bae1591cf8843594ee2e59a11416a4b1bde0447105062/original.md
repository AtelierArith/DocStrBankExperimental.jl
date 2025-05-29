```
J = jac_lin_op(nlp, x)
```

Return the linear Jacobian at `x` as a linear operator. The resulting object may be used as if it were a matrix, e.g., `J * v` or `J' * v`.
