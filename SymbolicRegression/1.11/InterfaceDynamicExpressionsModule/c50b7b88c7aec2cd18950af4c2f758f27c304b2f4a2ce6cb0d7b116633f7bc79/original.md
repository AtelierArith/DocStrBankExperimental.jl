```
eval_tree_array(tree::Union{AbstractExpression,AbstractExpressionNode}, X::AbstractArray, options::AbstractOptions; kws...)
```

Evaluate a binary tree (equation) over a given input data matrix. The operators contain all of the operators used. This function fuses doublets and triplets of operations for lower memory usage.

This function can be represented by the following pseudocode:

```
function eval(current_node)
    if current_node is leaf
        return current_node.value
    elif current_node is degree 1
        return current_node.operator(eval(current_node.left_child))
    else
        return current_node.operator(eval(current_node.left_child), eval(current_node.right_child))
```

The bulk of the code is for optimizations and pre-emptive NaN/Inf checks, which speed up evaluation significantly.

# Arguments

  * `tree::Union{AbstractExpression,AbstractExpressionNode}`: The root node of the tree to evaluate.
  * `X::AbstractArray`: The input data to evaluate the tree on.
  * `options::AbstractOptions`: Options used to define the operators used in the tree.

# Returns

  * `(output, complete)::Tuple{AbstractVector, Bool}`: the result,   which is a 1D array, as well as if the evaluation completed   successfully (true/false). A `false` complete means an infinity   or nan was encountered, and a large loss should be assigned   to the equation.
