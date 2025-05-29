```
read10x_matrix_metadata(io; transpose=false)
```

Read 10x (CellRanger) count matrix metadata. `io` can be filename (".h5" or ".mtx[.gz]") or an `HDF5.File` handle or an IO object.

Returns `(P,N,nnz)` the height, width and number of nonzero entries of the count matrix.

If `transpose` is `true`, then `P` and `N` are swapped.

See also: [`read10x`](@ref), [`read10x_matrix`](@ref)
