```
hl = passfail_highlighter(df, c=crayon"bold red")
```

A PrettyTables highlighter that colors failures in bold red by default.

### Input Arguments

  * `df::DataFrame` dataframe to which the highlighter will be applied.   `df` must have the `id` column.

If `df` has the `:status` property, the highlighter will be applied to rows for which `df.status` indicates a failure. A failure is any status different from `:first_order` or `:unbounded`.
