```
eval_grad_tree_array(tree::AbstractExpressionNode{T}, cX::AbstractMatrix{T}, operators::OperatorEnum; variable::Union{Bool,Val}=Val(false), turbo::Union{Bool,Val}=Val(false))
```

Compute the forward-mode derivative of an expression, using a similar structure and optimization to eval*tree*array. `variable` specifies whether we should take derivatives with respect to features (i.e., cX), or with respect to every constant in the expression.

# Arguments

  * `tree::AbstractExpressionNode{T}`: The expression tree to evaluate.
  * `cX::AbstractMatrix{T}`: The data matrix, with each column being a data point.
  * `operators::OperatorEnum`: The operators used to create the `tree`.
  * `variable::Union{Bool,Val}`: Whether to take derivatives with respect to features (i.e., `cX` - with `variable=true`),   or with respect to every constant in the expression (`variable=false`).
  * `turbo::Union{Bool,Val}`: Use LoopVectorization.jl for faster evaluation. Currently this does not have   any effect.

# Returns

  * `(evaluation, gradient, complete)::Tuple{AbstractVector{T}, AbstractMatrix{T}, Bool}`: the normal evaluation,   the gradient, and whether the evaluation completed as normal (or encountered a nan or inf).
