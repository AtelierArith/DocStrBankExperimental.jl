```
isempty(@nospecialize(ids::IDS), field::Symbol; include_expr::Bool=false, eval_expr::Bool=false)
```

Returns true if the ids field has no data (or expression)

NOTE: By default it does not include nor evaluate expressions
