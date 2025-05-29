```
readstatallmeta(filepath; kwargs...)
```

Return all metadata including value labels without reading the full data from a supported data file located at `filepath`. The four returned objects are for file-level metadata, variable names, variable-level metadata and value labels respectively. See also [`readstatmeta`](@ref).

# Supported File Formats

  * Stata: `.dta`
  * SAS: `.sas7bdat` and `.xpt`
  * SPSS: `.sav` and `por`

# Keywords

  * `ext = lowercase(splitext(filepath)[2])`: extension of data file for choosing the parser.
  * `usecols::Union{ColumnSelector, Nothing} = nothing`: only collect variable-level metadata from the specified columns (variables); collect all columns if `usecols=nothing`.
  * `file_encoding::Union{String, Nothing} = nothing`: manually specify the file character encoding; need to be an `iconv`-compatible name.
  * `handler_encoding::Union{String, Nothing} = nothing`: manually specify the handler character encoding; default to UTF-8.
