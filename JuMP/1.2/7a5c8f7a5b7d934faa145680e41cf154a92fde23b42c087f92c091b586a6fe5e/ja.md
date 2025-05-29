```
parse_constraint_call(
    _error::Function,
    vectorized::Bool,
    ::Val{op},
    lhs,
    rhs,
) where {op}
```

二項演算子のフォールバックハンドラ。これらは `@constraint(model, lhs op rhs)` のような中置演算子や、`@constraint(model, op(lhs, rhs))` のような通常の演算子である可能性があります。

どちらの場合も、`lhs - rhs in operator_to_set(_error, op)` として書き換えます。

詳細については [`operator_to_set`](@ref) を参照してください。
