```
get_unused_symbols(model::Model; filter_known_unused=false)
```

Returns a dictionary with vectors of the unused variables, shocks, and parameters.

Keyword arguments:

  * filter*known*unused::Bool - When `true`, the results will exclude variables present in model.option.unused_varshks. The default is `false`.
