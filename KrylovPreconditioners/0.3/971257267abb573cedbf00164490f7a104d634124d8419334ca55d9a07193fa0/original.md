```
update!(op::AbstractTriangularOperator, A)
```

Update the sparse matrix `A` associated with the given `AbstractTriangularOperator` without the need to reallocate buffers  or repeat the structural analysis phase for detecting parallelism for sparse triangular solves. `A` and the operator `op` must have the same sparsity pattern, enabling efficient reuse of existing resources.

#### Input arguments

  * `op`: The triangular operator to update;
  * `A`: The new sparse matrix to associate with the operator.
