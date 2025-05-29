```
show(io::IO, mime::MIME, df::AbstractDataFrame)
```

Render a data frame to an I/O stream in MIME type `mime`.

# Arguments

  * `io::IO`: The I/O stream to which `df` will be printed.
  * `mime::MIME`: supported MIME types are: `"text/plain"`, `"text/html"`, `"text/latex"`, `"text/csv"`, `"text/tab-separated-values"` (the last two MIME types do not support  showing `#undef` values)
  * `df::AbstractDataFrame`: The data frame to print.

Additionally selected MIME types support passing the following keyword arguments:

  * MIME type `"text/plain"` accepts all listed keyword arguments and their behavior is identical as for `show(::IO, ::AbstractDataFrame)`
  * MIME type `"text/html"` accepts the following keyword arguments:

      * `eltypes::Bool = true`: Whether to print the column types under column names.
      * `summary::Bool = true`: Whether to print a brief string summary of the data frame.
      * `max_column_width::AbstractString = ""`: The maximum column width. It must     be a string containing a valid CSS length. For example, passing     "100px" will limit the width of all columns to 100 pixels. If empty,     the columns will be rendered without limits.
      * `kwargs...`: Any keyword argument supported by the function `pretty_table` of PrettyTables.jl can be passed here to customize the output.

# Examples

```jldoctest
julia> show(stdout, MIME("text/latex"), DataFrame(A=1:3, B=["x", "y", "z"]))
\begin{tabular}{r|cc}
	& A & B\\
	\hline
	& Int64 & String\\
	\hline
	1 & 1 & x \\
	2 & 2 & y \\
	3 & 3 & z \\
\end{tabular}
14

julia> show(stdout, MIME("text/csv"), DataFrame(A=1:3, B=["x", "y", "z"]))
"A","B"
1,"x"
2,"y"
3,"z"
```
