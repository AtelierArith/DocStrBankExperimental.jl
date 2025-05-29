```
(tree::AbstractExpressionNode)(X, operators::GenericOperatorEnum; kws...)
```

# Arguments

  * `X::AbstractArray`: The input data to evaluate the tree on.
  * `operators::GenericOperatorEnum`: The operators used in the tree.
  * `kws...`: Passed to `eval_tree_array`.

# Returns

  * `output`: the result of the evaluation.   If evaluation failed, `nothing` will be returned for the first argument.   A `false` complete means an operator was called on input types   that it was not defined for. You can change this behavior by   setting `throw_errors=false`.
