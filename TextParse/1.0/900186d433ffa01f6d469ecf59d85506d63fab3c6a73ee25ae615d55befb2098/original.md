```
csvread(file::Union{String,IO}, delim=','; <arguments>...)
```

Read CSV from `file`. Returns a tuple of 2 elements:

1. A tuple of columns each either a `Vector`, or `StringArray`
2. column names if `header_exists=true`, empty array otherwise

# Arguments:

  * `file`: either an IO object or file name string
  * `delim`: the delimiter character
  * `spacedelim`: (Bool) parse space-delimited files. `delim` has no effect if true.
  * `quotechar`: character used to quote strings, defaults to `"`
  * `escapechar`: character used to escape quotechar in strings. (could be the same as quotechar)
  * `commentchar`: ignore lines that begin with commentchar
  * `row_estimate`: estimated number of rows in the file. Defaults to `0` in which case we try to estimate this.
  * `skiplines_begin`: skips specified number of lines at the beginning of the file
  * `header_exists`: boolean specifying whether CSV file contains a header
  * `nastrings`: strings that are to be considered NA. Defaults to `TextParse.NA_STRINGS`
  * `colnames`: manually specified column names. Could be a vector or a dictionary from Int index (the column) to String column name.
  * `colparsers`: Parsers to use for specified columns. This can be a vector or a dictionary from column name / column index (Int) to a "parser". The simplest parser is a type such as Int, Float64. It can also be a `dateformat"..."`, see [CustomParser](@ref) if you want to plug in custom parsing behavior. If you pass `nothing` as the parser for a given column, that column will be skipped
  * `type_detect_rows`: number of rows to use to infer the initial `colparsers` defaults to 20.
