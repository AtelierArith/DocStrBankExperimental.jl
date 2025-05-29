```
read10x_features(io, [featuretype=NamedTuple]; [guess, delim])
```

Read 10x features. `io` can be a filename (".h5", ".tsv[.gz]", ".csv[.gz]" or ".mtx[.gz]") or an `HDF5.File` handle or an IO object.

The returned annotation table for features is of the type `featuretype` and can be one of:

  * NamedTuple - With column names as keys and column vectors as values.
  * DataFrame - See `DataFrames` package.
  * Other table types that can be constructed from NamedTuples.
  * A user defined function/type constructor taking a NamedTuple as input.

If the input filename is "[prefix]matrix.mtx[.gz]", then the same folder will be searched for a matching feature file. Set `guess=nothing` to disable. `guess` can also be set to a function taking the matrix file path as input and returning the corresponding feature file path.

The column delimiter `delim` will be detected from the file name if not specifed.

See also: [`read10x`](@ref), [`read10x_matrix`](@ref), [`read10x_barcodes`](@ref)
