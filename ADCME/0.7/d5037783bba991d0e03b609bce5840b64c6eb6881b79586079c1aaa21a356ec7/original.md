```
adjoint(A::mpi_SparseTensor)
```

Returns the adjoint of `A`, i.e., `A'`. Each MPI rank owns the same number of rows.
