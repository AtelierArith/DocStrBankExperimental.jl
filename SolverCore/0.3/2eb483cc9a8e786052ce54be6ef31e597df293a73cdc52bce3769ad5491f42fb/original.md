```
log_header(colnames, coltypes)
```

Creates a header using the names in `colnames` formatted according to the types in `coltypes`. Uses internal formatting specification given by `SolverCore.formats` and default header translation given by `SolverCore.default_headers`.

Input:

  * `colnames::Vector{Symbol}`: Column names.
  * `coltypes::Vector{DataType}`: Column types.

Keyword arguments:

  * `hdr_override::Dict{Symbol,String}`: Overrides the default headers.
  * `colsep::Int`: Number of spaces between columns (Default: 2)

See also [`log_row`](@ref).
