```
count_scalar_constants(tree::AbstractExpressionNode{T})::Int64 where {T}
```

Counts the number of scalar constants in the tree. Used in get*scalar*constants to preallocate a vector for storing constants array.
