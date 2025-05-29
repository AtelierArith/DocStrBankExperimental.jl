```
render_expr(ex::AbstractExpression{T}, options::AbstractOptions) -> String
```

Given an AbstractExpression and an options object, return a string representation of the expression. Specifically, replace constants with "C" and variables with "x", "y", "z", etc or the prespecified variable names.
