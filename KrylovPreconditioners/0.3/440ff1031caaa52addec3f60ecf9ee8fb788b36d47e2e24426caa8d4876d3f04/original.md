```
update!(op::AbstractKrylovOperator, A)
```

Update the sparse matrix `A` associated with the given `AbstractKrylovOperator` without the need to reallocate buffers  or repeat the structural analysis phase for detecting parallelism for sparse matrix-vector or matrix-matrix products. `A` and the operator `op` must have the same sparsity pattern, enabling efficient reuse of existing resources.

#### Input arguments

  * `op`: The Krylov operator to update;
  * `A`: The new sparse matrix to associate with the operator.
