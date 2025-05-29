```
keys_no_missing(@nospecialize(ids::IDS); include_expr::Bool=true, eval_expr::Bool=false)
```

Returns generator of fields with data in a IDS

NOTE: By default it includes expressions, but does not evaluate them. It assumes that a IDStop without data will also have no valid expressions.
