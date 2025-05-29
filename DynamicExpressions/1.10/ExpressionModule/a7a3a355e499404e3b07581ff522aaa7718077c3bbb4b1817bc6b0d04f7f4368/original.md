```
string_tree(
    ex::AbstractExpression,
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    variable_names=nothing,
    kws...
)
```

Convert an expression to a string representation.

This method unpacks the operators and variable names from the expression and calls [`string_tree`](@ref StringsModule.string_tree) for `AbstractExpressionNode`.

# Arguments

  * `ex`: The expression to convert to a string.
  * `operators`: (Optional) Operators to use. If `nothing`, operators are obtained from the expression.
  * `variable_names`: (Optional) Variable names to use in the string representation. If `nothing`, variable names are obtained from the expression.
  * `kws...`: Additional keyword arguments.

# Returns

  * A string representation of the expression.
