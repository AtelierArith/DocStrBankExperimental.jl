```
displaytable([io::IO], v::AbstractVector{T}; kwargs...)
```

Display a vector of things in a compact tabular format. The `io` argument is defaulted to `stdout`.

# Keyword arguments

  * padding: minimum number of spaces between column data. Default value is 2.
  * index: prepend cell values with indices. Default value is `false`.
  * indexsep: string that separate index and cell values.  Default value is `:`.
  * align: either `:left` or `:right`.  Default value is `:left`.
  * orientation: either `:column` or `:row`.  Default value is `:column`.
  * formatter: custom formatter that takes a value and returns a string.  Default value is `string` function.
  * displaywidth: custom display width.  Default value is 0, for which the system will use the terminal's size.

# Examples

```
displaytable([string("randomstr", i) for i in 1:56])

using Formatting
foo = generate_formatter("%7.5f")
displaytable(rand(100); padding=5, align=:right, formatter=foo, index=true, indexsep=" -> ")
```
