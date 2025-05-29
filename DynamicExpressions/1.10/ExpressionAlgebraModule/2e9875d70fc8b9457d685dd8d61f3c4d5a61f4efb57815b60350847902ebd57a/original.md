```
@declare_expression_operator(op, arity)
```

Declare an operator function for `AbstractExpression` types.

This macro generates a method for the given operator `op` that works with `AbstractExpression` arguments. The `arity` parameter specifies whether the operator is unary (1) or binary (2).

# Arguments

  * `op`: The operator to be declared (e.g., `Base.sin`, `Base.:+`).
  * `arity`: The number of arguments the operator takes (1 for unary, 2 for binary).
