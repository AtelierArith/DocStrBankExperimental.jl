```
parse_one_operator_variable(
    error_fn::Function,
    info_expr::_VariableInfoExpr,
    sense::Val{S},
    value,
) where {S}
```

`@variable` マクロの形式 `variable name S value` の変数式に対して `infoexr` を更新します。
