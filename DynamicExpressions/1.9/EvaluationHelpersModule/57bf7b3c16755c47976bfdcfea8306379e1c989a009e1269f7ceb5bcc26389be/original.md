```
(tree::AbstractExpressionNode)(X, operators::OperatorEnum; kws...)
```

Evaluate a binary tree (equation) over a given input data matrix. The operators contain all of the operators used. This function fuses doublets and triplets of operations for lower memory usage.

# Arguments

  * `tree::AbstractExpressionNode`: The root node of the tree to evaluate.
  * `X::AbstractMatrix{T}`: The input data to evaluate the tree on, with shape `[num_features, num_rows]`.
  * `operators::OperatorEnum`: The operators used in the tree.
  * `kws...`: Passed to `eval_tree_array`.

# Returns

  * `output::AbstractVector{T}`: the result, which is a 1D array.   Any NaN, Inf, or other failure during the evaluation will result in the entire   output array being set to NaN.
