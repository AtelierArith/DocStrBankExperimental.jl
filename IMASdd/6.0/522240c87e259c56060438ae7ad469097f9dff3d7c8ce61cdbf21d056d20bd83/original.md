```
isempty(@nospecialize(ids::IDS); include_expr::Bool=false, eval_expr::Bool=false)
```

Returns true if none of the IDS fields downstream have data (or expressions)

NOTE: By default it does not include nor evaluate expressions
