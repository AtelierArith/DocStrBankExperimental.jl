```
get_sparse_dof_map(trial::FESpace,test::FESpace,args...) -> AbstractDofMap
```

Returns the index maps related to Jacobiansin a FE problem. The default output is a `TrivialSparseMatrixDofMap`; when the trial and test spaces are of type `TProductFESpace`, a `SparseMatrixDofMap` is returned.
