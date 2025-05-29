```
get_scalar_constants(tree::AbstractExpressionNode{T}, BT::Type = T)::Vector{T} where {T}
```

Get all the scalar constants inside a tree, in depth-first order. The function `set_scalar_constants!` sets them in the same order, given the output of this function. Also return metadata that can will be used in the `set_scalar_constants!` function.
