```
pretty_latex_stats(df; kwargs...)
```

Pretty-print a DataFrame as a LaTeX longtable using PrettyTables.

See the `pretty_stats` documentation. Specific settings in this method are:

  * the backend is set to `:latex`;
  * the table type is set to `:longtable`;
  * highlighters, if any, should be LaTeX highlighters.

See the PrettyTables documentation for more information.
