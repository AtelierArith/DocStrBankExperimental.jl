```
show([io::IO, ]df::AbstractDataFrame;
     allrows::Bool = !get(io, :limit, false),
     allcols::Bool = !get(io, :limit, false),
     allgroups::Bool = !get(io, :limit, false),
     rowlabel::Symbol = :Row,
     summary::Bool = true,
     eltypes::Bool = true,
     truncate::Int = 32,
     kwargs...)
```

Render a data frame to an I/O stream. The specific visual representation chosen depends on the width of the display.

If `io` is omitted, the result is printed to `stdout`, and `allrows`, `allcols` and `allgroups` default to `false`.

# Arguments

  * `io::IO`: The I/O stream to which `df` will be printed.
  * `df::AbstractDataFrame`: The data frame to print.
  * `allrows::Bool`: Whether to print all rows, rather than a subset that fits the device height. By default this is the case only if `io` does not have the `IOContext` property `limit` set.
  * `allcols::Bool`: Whether to print all columns, rather than a subset that fits the device width. By default this is the case only if `io` does not have the `IOContext` property `limit` set.
  * `allgroups::Bool`: Whether to print all groups rather than the first and last, when `df` is a `GroupedDataFrame`. By default this is the case only if `io` does not have the `IOContext` property `limit` set.
  * `rowlabel::Symbol = :Row`: The label to use for the column containing row numbers.
  * `summary::Bool = true`: Whether to print a brief string summary of the data frame.
  * `eltypes::Bool = true`: Whether to print the column types under column names.
  * `truncate::Int = 32`: the maximal display width the output can use before being truncated (in the `textwidth` sense, excluding `…`). If `truncate` is 0 or less, no truncation is applied.
  * `kwargs...`: Any keyword argument supported by the function `pretty_table` of PrettyTables.jl can be passed here to customize the output.

# Examples

```jldoctest
julia> using DataFrames

julia> df = DataFrame(A=1:3, B=["x", "y", "z"]);

julia> show(df, show_row_number=false)
3×2 DataFrame
 A      B
 Int64  String
───────────────
     1  x
     2  y
     3  z
```
