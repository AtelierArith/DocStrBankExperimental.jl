### readpetsc(filename; int*type = nothing, scalar*type = nothing)

```
       :: Vector{Union{SparseMatrixCSC, Vector}}
```

Read a sparse matrix in PETSc's binary format from `filename`. PETSC*DIR and PETSC*ARCH will be used to determine the correct integer and float type to use. `int_type` and `scalar_type` can be used to override these values.
