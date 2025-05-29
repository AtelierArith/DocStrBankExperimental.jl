```
PyPandasDataFrame(x; [indexname::Union{Nothing,Symbol}], [columnnames::Function], [columntypes::Function])
```

Wraps the pandas DataFrame `x` as a Tables.jl-compatible table.

  * `indexname`: The name of the column including the index. The default is `nothing`, meaning to exclude the index.
  * `columnnames`: A function mapping the Python column name (a `Py`) to the Julia one (a `Symbol`). The default is `x -> Symbol(x)`.
  * `columntypes`: A function taking the column name (a `Symbol`) and returning either the desired element type of the column, or `nothing` to indicate automatic inference.
