```
(ex::AbstractExpression)(X, operators::Union{AbstractOperatorEnum,Nothing}=nothing; kws...)
```

Evaluate the expression `ex` over the input data `X`.

This method unpacks the operators from the expression and calls the corresponding method for `AbstractExpressionNode`.

# Arguments

  * `X`: The input data to evaluate the expression on.
  * `operators`: (Optional) Operators to use. If `nothing`, operators are obtained from the expression.
  * `kws...`: Additional keyword arguments.

# Returns

  * The result of evaluating the expression over the input data `X`.
