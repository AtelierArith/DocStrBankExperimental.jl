```
ex = definition(Expr, method::Method)
ex = definition(method::Method)
```

Return an expression that defines `method`. If the definition can't be found, returns `nothing`.

See also [`code_expr`](@ref).
