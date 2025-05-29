```
read10x_barcodes(io, [barcodetype=Vector]; [guess, delim])
```

Read 10x barcodes. `io` can be a filename (".h5", ".tsv[.gz]", ".csv[.gz]" or "[prefix]matrix.mtx[.gz]") or an `HDF5.File` handle or an IO object.

The returned annotation object for barcodes is of the type `barcodetype` and can be one of:

  * Vector - With barcode values for each cell.
  * NamedTuple - With "barcode" as key, and barcode vector as value.
  * DataFrame - See `DataFrames` package.
  * Other table types that can be constructed from NamedTuples.
  * A user defined function/type constructor taking a NamedTuple as input.

If the input filename is "[prefix]matrix.mtx[.gz]", then the same folder will be searched for a matching barcode file. Set `guess=nothing` to disable. `guess` can also be set to a function taking the matrix file path as input and returning the corresponding barcode file path.

The column delimiter `delim` will be detected from the file name if not specifed.

See also: [`read10x`](@ref), [`read10x_matrix`](@ref), [`read10x_features`](@ref)
