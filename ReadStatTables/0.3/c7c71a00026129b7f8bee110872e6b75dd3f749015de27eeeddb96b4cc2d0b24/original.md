```
readstat(filepath; kwargs...)
```

Return a [`ReadStatTable`](@ref) that collects data (including metadata) from a supported data file located at `filepath`.

# Supported File Formats

  * Stata: `.dta`
  * SAS: `.sas7bdat` and `.xpt`
  * SPSS: `.sav` and `por`

# Keywords

  * `ext = lowercase(splitext(filepath)[2])`: extension of data file for choosing the parser.
  * `usecols::Union{ColumnSelector, Nothing} = nothing`: only collect data from the specified columns (variables); collect all columns if `usecols=nothing`.
  * `row_limit::Union{Integer, Nothing} = nothing`: restrict the total number of rows to be read; read all rows if `row_limit=nothing`.
  * `row_offset::Integer = 0`: skip the specified number of rows.
  * `ntasks::Union{Integer, Nothing} = nothing`: number of tasks spawned to read data file in concurrent chunks with multiple threads; with `ntasks` being `nothing` or smaller than 1, select a default value based on the size of data file and the number of threads available (`Threads.nthreads()`); not applicable to `.xpt` and `.por` files where row count is unknown from metadata.
  * `apply_value_labels::Bool = true`: apply value labels to the associated columns.
  * `inlinestring_width::Integer = ext ∈ (".sav", ".por") ? 0 : 32`: use a fixed-width string type that can be stored inline for any string variable with width below `inlinestring_width` and `pool_width`; a non-positive value avoids using any inline string type; not recommended for SPSS files.
  * `pool_width::Integer = 64`: only attempt to use `PooledArray` for string variables with width of at least 64.
  * `pool_thres::Integer = 500`: do not use `PooledArray` for string variables if the number of unique values exceeds `pool_thres`; a non-positive value avoids using `PooledArray`.
  * `file_encoding::Union{String, Nothing} = nothing`: manually specify the file character encoding; need to be an `iconv`-compatible name.
  * `handler_encoding::Union{String, Nothing} = nothing`: manually specify the handler character encoding; default to UTF-8.
