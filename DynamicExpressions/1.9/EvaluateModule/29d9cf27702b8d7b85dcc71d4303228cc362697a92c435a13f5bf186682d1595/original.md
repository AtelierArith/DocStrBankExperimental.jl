```
eval_tree_array(tree::AbstractExpressionNode, cX::AbstractMatrix, operators::GenericOperatorEnum; throw_errors::Bool=true)
```

Evaluate a generic binary tree (equation) over a given input data, whatever that input data may be. The `operators` enum contains all of the operators used. Unlike `eval_tree_array` with the normal `OperatorEnum`, the array `cX` is sliced only along the first dimension. i.e., if `cX` is a vector, then the output of a feature node will be a scalar. If `cX` is a 3D tensor, then the output of a feature node will be a 2D tensor. Note also that `tree.feature` will index along the first axis of `cX`.

However, there is no requirement about input and output types in general. You may set up your tree such that some operator nodes work on tensors, while other operator nodes work on scalars. `eval_tree_array` will simply return `nothing` if a given operator is not defined for the given input type.

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

# Arguments

  * `tree::AbstractExpressionNode`: The root node of the tree to evaluate.
  * `cX::AbstractArray`: The input data to evaluate the tree on.
  * `operators::GenericOperatorEnum`: The operators used in the tree.
  * `throw_errors::Bool=true`: Whether to throw errors   if they occur during evaluation. Otherwise,   MethodErrors will be caught before they happen and    evaluation will return `nothing`,   rather than throwing an error. This is useful in cases   where you are unsure if a particular tree is valid or not,   and would prefer to work with `nothing` as an output.

# Returns

  * `(output, complete)::Tuple{Any, Bool}`: the result,   as well as if the evaluation completed successfully (true/false).   If evaluation failed, `nothing` will be returned for the first argument.   A `false` complete means an operator was called on input types   that it was not defined for.
