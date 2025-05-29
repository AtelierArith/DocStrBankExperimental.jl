```
read10x_matrix(io, [matrixtype=SparseMatrixCSC{Int,Int}; transpose=false)
```

Read 10x (CellRanger) count matrix. `io` can be filename (".h5" or ".mtx[.gz]") or an `HDF5.File` handle or an IO object.

The returned count matrix is of type `matrixtype` and can be one of:

  * `SparseMatrixCSC` - The standard sparse matrix format in Julia, found in `SparseArrays`.
  * `Matrix` - A standard dense matrix.

If `transpose` is `true`, the data matrix will be read transposed.

See also: [`read10x`](@ref), [`read10x_barcodes`](@ref), [`read10x_features`](@ref)
