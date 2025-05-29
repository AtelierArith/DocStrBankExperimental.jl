```
readstatmeta(filepath; kwargs...)
```

Return a [`ReadStatMeta`](@ref) that collects file-level metadata without reading the full data from a supported data file located at `filepath`. See also [`readstatallmeta`](@ref).

# Supported File Formats

  * Stata: `.dta`
  * SAS: `.sas7bdat` and `.xpt`
  * SPSS: `.sav` and `por`

# Keywords

  * `ext = lowercase(splitext(filepath)[2])`: extension of data file for choosing the parser.
  * `file_encoding::Union{String, Nothing} = nothing`: manually specify the file character encoding; need to be an `iconv`-compatible name.
  * `handler_encoding::Union{String, Nothing} = nothing`: manually specify the handler character encoding; default to UTF-8.
