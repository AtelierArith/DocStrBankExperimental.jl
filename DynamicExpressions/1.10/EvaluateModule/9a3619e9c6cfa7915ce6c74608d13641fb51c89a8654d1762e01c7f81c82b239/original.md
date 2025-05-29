```
eval_tree_array(
    tree::AbstractExpressionNode{T},
    cX::AbstractMatrix{T},
    operators::OperatorEnum;
    eval_options::Union{EvalOptions,Nothing}=nothing,
) where {T}
```

Evaluate a binary tree (equation) over a given input data matrix. The operators contain all of the operators used. This function fuses doublets and triplets of operations for lower memory usage.

# Arguments

  * `tree::AbstractExpressionNode`: The root node of the tree to evaluate.
  * `cX::AbstractMatrix{T}`: The input data to evaluate the tree on, with shape `[num_features, num_rows]`.
  * `operators::OperatorEnum`: The operators used in the tree.
  * `eval_options::Union{EvalOptions,Nothing}`: See [`EvalOptions`](@ref) for documentation   on the different evaluation modes.

# Returns

  * `(output, complete)::Tuple{AbstractVector{T}, Bool}`: the result,   which is a 1D array, as well as if the evaluation completed   successfully (true/false). A `false` complete means an infinity   or nan was encountered, and a large loss should be assigned   to the equation.

# Notes

This function can be represented by the following pseudocode:

```
def eval(current_node)
    if current_node is leaf
        return current_node.value
    elif current_node is degree 1
        return current_node.operator(eval(current_node.left_child))
    else
        return current_node.operator(eval(current_node.left_child), eval(current_node.right_child))
```

The bulk of the code is for optimizations and pre-emptive NaN/Inf checks, which speed up evaluation significantly.
