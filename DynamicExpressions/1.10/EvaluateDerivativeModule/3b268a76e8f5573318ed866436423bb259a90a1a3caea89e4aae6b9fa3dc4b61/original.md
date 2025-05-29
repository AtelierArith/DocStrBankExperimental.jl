```
eval_diff_tree_array(
    tree::AbstractExpressionNode{T},
    cX::AbstractMatrix{T},
    operators::OperatorEnum,
    direction::Integer;
    turbo::Union{Bool,Val}=Val(false)
) where {T<:Number}
```

Compute the forward derivative of an expression, using a similar structure and optimization to eval*tree*array. `direction` is the index of a particular variable in the expression. e.g., `direction=1` would indicate derivative with respect to `x1`.

# Arguments

  * `tree::AbstractExpressionNode`: The expression tree to evaluate.
  * `cX::AbstractMatrix{T}`: The data matrix, with shape `[num_features, num_rows]`.
  * `operators::OperatorEnum`: The operators used to create the `tree`.
  * `direction::Integer`: The index of the variable to take the derivative with respect to.
  * `turbo::Union{Bool,Val}`: Use LoopVectorization.jl for faster evaluation. Currently this does not have   any effect.

# Returns

  * `(evaluation, derivative, complete)::Tuple{AbstractVector{T}, AbstractVector{T}, Bool}`: the normal evaluation,   the derivative, and whether the evaluation completed as normal (or encountered a nan or inf).
