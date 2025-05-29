```
eval_grad_tree_array(tree::Union{AbstractExpression,AbstractExpressionNode}, X::AbstractArray, options::AbstractOptions; variable::Bool=false)
```

Compute the forward-mode derivative of an expression, using a similar structure and optimization to eval*tree*array. `variable` specifies whether we should take derivatives with respect to features (i.e., `X`), or with respect to every constant in the expression.

# Arguments

  * `tree::Union{AbstractExpression,AbstractExpressionNode}`: The expression tree to evaluate.
  * `X::AbstractArray`: The data matrix, with each column being a data point.
  * `options::AbstractOptions`: The options containing the operators used to create the `tree`.
  * `variable::Bool`: Whether to take derivatives with respect to features (i.e., `X` - with `variable=true`),   or with respect to every constant in the expression (`variable=false`).

# Returns

  * `(evaluation, gradient, complete)::Tuple{AbstractVector, AbstractArray, Bool}`: the normal evaluation,   the gradient, and whether the evaluation completed as normal (or encountered a nan or inf).
