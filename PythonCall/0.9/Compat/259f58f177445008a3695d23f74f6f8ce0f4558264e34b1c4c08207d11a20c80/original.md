```
pytable(src, format=:pandas; ...)
```

Construct a Python table from the Tables.jl-compatible table `src`.

The `format` controls the type of the resulting table, and is one of:

  * `:pandas`: A `pandas.DataFrame`. Keyword arguments are passed to the `DataFrame` constructor.
  * `:columns`: A `dict` mapping column names to columns.
  * `:rows`: A `list` of rows, which are `namedtuple`s.
  * `:rowdicts`: A `list` of rows, which are `dict`s.
