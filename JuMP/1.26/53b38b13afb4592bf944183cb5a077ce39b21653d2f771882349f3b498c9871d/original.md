```
parse_one_operator_variable(
    error_fn::Function,
    info_expr::_VariableInfoExpr,
    sense::Val{S},
    value,
) where {S}
```

Update `infoexr` for a variable expression in the `@variable` macro of the form `variable name S value`.
