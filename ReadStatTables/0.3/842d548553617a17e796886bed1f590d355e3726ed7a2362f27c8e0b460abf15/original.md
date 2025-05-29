```
writestat(filepath, table; ext = lowercase(splitext(filepath)[2]), kwargs...)
```

Write a `Tables.jl`-compatible `table` to `filepath` as a data file supported by `ReadStat`. File format is determined based on the extension contained in `filepath` and may be overriden by the `ext` keyword.

Any user-provided `table` is converted to a [`ReadStatTable`](@ref) first before being handled by a `ReadStat` writer. Therefore, to gain fine-grained control over the content to be written, especially for metadata, one may directly work with a [`ReadStatTable`](@ref) (possibly converted from another table type such as `DataFrame` from `DataFrames.jl`) before passing it to `writestat`. Alternatively, one may pass any keyword argument accepted by a constructor of [`ReadStatTable`](@ref) to `writestat`. The actual [`ReadStatTable`](@ref) handled by the writer is returned after the writer finishes.

# Supported File Formats

  * Stata: `.dta`
  * SAS: `.sas7bdat` and `.xpt` (Note: SAS may not recognize the produced `.sas7bdat` files due to a known limitation with ReadStat.)
  * SPSS: `.sav` and `por`

# Conversion

For data values, Julia objects are converted to the closest `ReadStat` type for either numerical values or strings. However, depending on the file format of the output file, a data column may be written in a different type when the closest `ReadStat` type is not supported.

For metadata, if the user-provided `table` is not a [`ReadStatTable`](@ref), an attempt will be made to collect table-level or column-level metadata with a key that matches a metadata field in [`ReadStatMeta`](@ref) or [`ReadStatColMeta`](@ref) via the `metadata` and `colmetadata` interface defined by `DataAPI.jl`. If the `table` is a [`ReadStatTable`](@ref), then the associated metadata will be written as long as their values are compatible with the format of the output file. Value labels associated with a [`LabeledArray`](@ref) are always preserved even when the name of the dictionary of value labels is not specified in metadata (column name will be used by default). If a column is of an array type that makes use of `DataAPI.refpool` (e.g., `CategoricalArray` and `PooledArray`), value labels will be generated automatically by default (with keyword `refpoolaslabel` set to be `true`) and the underlying numerical reference values instead of the values returned by `getindex` are written to files (with value labels attached).
