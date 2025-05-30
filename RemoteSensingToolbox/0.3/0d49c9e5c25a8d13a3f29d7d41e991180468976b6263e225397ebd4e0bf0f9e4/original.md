```
from_table(table, val_col, dim_col, dims; missingval=0)
```

Read a table into a `Raster` or `RasterStack`.

# Parameters

  * `table`: Any type that implements the `Tables.jl` interface.
  * `val_col`: The column(s) containing the raster values. Must be either a Symbol or Tuple of Symbols.
  * `dim_col`: The column(s) containing the coordinates of each value. Should be a Symbol if the coordinates

are stored as Tuples under a single column. It can also be a Tuple of Symbols if coordinates are stored as scalar values across multuple columns.

  * `dims`: The dimensions of the output raster.
  * `missingval`: The value used to denote missing data.

# Returns

Returns a single `Raster` with the same dimensions as `dims` when `val_col` is a `Symbol`. Otherwise, returns a `RasterStack` in which each layer corresponds to a single value column.
