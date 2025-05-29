```
show_params(io::IO, pip::ParameterIndexingProxy; num_rows = 20, show_all = false, scalarize = true, kwargs...)
```

Method for customizing the table output. Keyword args:

  * num_rows
  * show*all: whether to show all parameters. Overrides `num*rows`.
  * scalarize: whether to scalarize array symbolics in the table output.
  * kwargs... are passed to the pretty_table call.
