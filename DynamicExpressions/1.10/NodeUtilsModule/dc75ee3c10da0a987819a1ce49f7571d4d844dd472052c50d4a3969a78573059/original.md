```
set_scalar_constants!(tree::AbstractExpressionNode{T}, constants, refs) where {T}
```

Set the constants in a tree, in depth-first order. The function `get_scalar_constants` gets them in the same order.
