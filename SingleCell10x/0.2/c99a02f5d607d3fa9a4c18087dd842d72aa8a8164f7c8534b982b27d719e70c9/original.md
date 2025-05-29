```
read10x(io, [matrixtype=SparseMatrixCSC{Int,Int}, featuretype=NamedTuple, barcodetype=Vector];
        transpose=false, [features, barcodes, delim])
```

Read 10x (CellRanger) count matrix and annotations. `io` can be filename (".h5" or "[prefix]matrix.mtx[.gz]") or an `HDF5.File` handle. NB: If the input filename is "[prefix]matrix.mtx[.gz]", the same folder will be searched for matching feature and barcode files.

The returned count matrix is of type `matrixtype` and can be one of:

  * `SparseMatrixCSC` - The standard sparse matrix format in Julia, found in `SparseArrays`.
  * `Matrix` - A standard dense matrix.

The returned annotations for barcodes/features are of types `barcodetype`/`featuretype` and can be one of:

  * NamedTuple - With column names as keys and column vectors as values.
  * Vector - For barcodes only.
  * DataFrame - See `DataFrames` package.
  * Other table types that can be constructed from NamedTuples.
  * A user defined function/type constructor taking a NamedTuple (features) or Vector (barcodes) as input.

If `transpose` is `true`, the data matrix will be read transposed.

`features` and `barcodes` are only allowed for `mtx[.gz]` files. They can be used to specify the file paths for `features`/`barcodes`. By default, the file paths will be autodetected. Set to `nothing` to disable. They can also be set to functions taking the matrix file path as input and returning the corresponding barcode/feature file path.

The column delimiter `delim` is only used for features/barcodes.(tsv|csv) files, and will be detected from the file name if not specifed.

See also: [`read10x_matrix`](@ref), [`read10x_barcodes`](@ref), [`read10x_features`](@ref)
