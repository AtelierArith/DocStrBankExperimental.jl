```
symbolic_evaluate(expr, syms::Dict; kwargs...)
```

Return the value of symbolic expression `expr` where the values of variables involved are obtained from the dictionary `syms`. The keys of `syms` are symbolic variables (not expressions of variables). The values of `syms` can be values or symbolic expressions.

The returned value should either be a value or an expression involving symbolic variables not present as keys in `syms`.

The function can take additional keyword arguments to control implementation-specific behavior.

This is already implemented for  `symbolic_evaluate(expr::Union{Symbol, Expr}, syms::Dict)`.
