```
parse_constraint_call(
    error_fn::Function,
    vectorized::Bool,
    ::Val{op},
    lhs,
    rhs,
) where {op}
```

二項演算子のフォールバックハンドラです。これらは `@constraint(model, lhs op rhs)` のような中置演算子や、`@constraint(model, op(lhs, rhs))` のような通常の演算子である可能性があります。

どちらの場合も、`lhs - rhs in operator_to_set(error_fn, op)` として書き換えます。

詳細については [`operator_to_set`](@ref) を参照してください。
