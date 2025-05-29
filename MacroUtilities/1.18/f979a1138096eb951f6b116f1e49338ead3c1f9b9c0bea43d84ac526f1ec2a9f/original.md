```
ExprWOptionalRhs{E <: AbstractExpr}(; lhs::E, default=not_provided)
```

Matches an expression of the form `lhs = default`, where `lhs` is matched by `E`, or an expression matched by `E`
