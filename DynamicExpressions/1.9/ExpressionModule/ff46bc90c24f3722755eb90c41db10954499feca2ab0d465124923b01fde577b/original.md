```
eval_tree_array(
    ex::AbstractExpression,
    cX::AbstractMatrix,
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    kws...
)
```

Evaluate an expression over a given input data matrix.

This method unpacks the operators from the expression and calls [`eval_tree_array`](@ref EvaluateModule.eval_tree_array) for `AbstractExpressionNode`.

# Arguments

  * `ex`: The expression to evaluate.
  * `cX`: The input data matrix.
  * `operators`: (Optional) Operators to use. If `nothing`, operators are obtained from the expression.
  * `kws...`: Additional keyword arguments.

# Returns

  * A tuple `(output, complete)` indicating the result and success of the evaluation.
