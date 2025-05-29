```
eval_diff_tree_array(tree::Union{AbstractExpression,AbstractExpressionNode}, X::AbstractArray, options::AbstractOptions, direction::Int)
```

Compute the forward derivative of an expression, using a similar structure and optimization to eval*tree*array. `direction` is the index of a particular variable in the expression. e.g., `direction=1` would indicate derivative with respect to `x1`.

# Arguments

  * `tree::Union{AbstractExpression,AbstractExpressionNode}`: The expression tree to evaluate.
  * `X::AbstractArray`: The data matrix, with each column being a data point.
  * `options::AbstractOptions`: The options containing the operators used to create the `tree`.
  * `direction::Int`: The index of the variable to take the derivative with respect to.

# Returns

  * `(evaluation, derivative, complete)::Tuple{AbstractVector, AbstractVector, Bool}`: the normal evaluation,   the derivative, and whether the evaluation completed as normal (or encountered a nan or inf).
