```
load10x(filename; lazy=false, var_id=nothing, var_id_delim='_')
```

Load a CellRanger ".h5" or ".mtx[.gz]" file as a DataMatrix.

  * `lazy` - If `true`, the count matrix itself will not be loaded, only features and barcodes. This is used internally in `load_counts` to merge samples more efficiently. Use `load_counts` to later load the count data.
  * `var_id` - If a pair `var_id_col=>cols`, the contents of columns `cols` will be merged to create new IDs. Useful to ensure that IDs are unique.
  * `var_id_delim` - Delimiter used to when merging variable columns to create the variable id column.

# Examples

Load counts from a CellRanger ".h5" file. (Recommended.)

```julia
julia> counts = load10x("filtered_feature_bc_matrix.h5")
```

Load counts from a CellRanger ".mtx" file. Tries to find barcode and feature annotation files in the same folder.

```julia
julia> counts = load10x("matrix.mtx.gz")
```

Lazy loading followed by loading.

```julia
julia> counts = load10x("filtered_feature_bc_matrix.h5");
julia> counts = load_counts(counts)
```

See also: [`load_counts`](@ref)
