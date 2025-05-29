```
eval_grad_tree_array(
    ex::AbstractExpression,
    cX::AbstractMatrix,
    operators::Union{AbstractOperatorEnum,Nothing}=nothing;
    kws...
)
```

Compute the forward-mode derivative of an expression.

This method unpacks the operators from the expression and calls [`eval_grad_tree_array`](@ref EvaluateDerivativeModule.eval_grad_tree_array) for `AbstractExpressionNode`.

# Arguments

  * `ex`: The expression to evaluate.
  * `cX`: The data matrix.
  * `operators`: (Optional) Operators to use. If `nothing`, operators are obtained from the expression.
  * `kws...`: Additional keyword arguments.

# Returns

  * A tuple `(output, gradient, complete)` indicating the result, gradient, and success of the evaluation.
