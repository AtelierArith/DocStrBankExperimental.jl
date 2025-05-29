```
AbstractExpression{T,N}
```

(Experimental) Abstract type for user-facing expression types, which contain both the raw expression tree operating on a value type of `T`, as well as associated metadata to evaluate and render the expression.

See [`ExpressionInterface`](@ref DynamicExpressions.InterfacesModule.ExpressionInterface) for a full description of the interface implementation, as well as tests to verify correctness.

If you wish to use `@parse_expression`, you can also customize the parsing behavior with

  * `parse_leaf`
