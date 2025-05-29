```
get_contents(ex::AbstractExpression)
```

Get the contents of the expression, which might be a plain `AbstractExpressionNode`, or some combination of them, or other data. This should include everything other than that returned by [`get_metadata`](@ref).
