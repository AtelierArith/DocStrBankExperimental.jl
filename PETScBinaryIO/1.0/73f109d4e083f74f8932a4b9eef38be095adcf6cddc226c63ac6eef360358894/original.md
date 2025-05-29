### writepetsc(filename, mat :: Vector{Union{SparseMatrixCSC, Vector}}; int*type = nothing, scalar*type = nothing)

Write a sparse matrix or vector to `filename` in a format PETSc can understand. `PETSC_DIR` and `PETSC_ARCH` will be used to determine the size of types written. `int_type` and `scalar_type` can be used to manually specify which types are desired.
