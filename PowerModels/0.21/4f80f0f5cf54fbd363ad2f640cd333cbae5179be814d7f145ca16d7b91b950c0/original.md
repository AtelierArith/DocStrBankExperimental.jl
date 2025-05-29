```
calc_susceptance_matrix_inv(data)
```

Compute the inverse of the network's susceptance matrix.

Note: `data`` should be a PowerModels network data model; only supports networks with exactly one refrence bus.

While the susceptance matrix is sparse, its inverse it typically quite dense. This implementation first computes a sparse factorization, then recovers the (dense)     matrix inverse via backward substitution. This is more efficient     than directly computing a dense inverse with `LinearAlgebra.inv`.
