```
svd(T::BlockSparseTensor{<:Number,2}; kwargs...)
```

svd of an order-2 BlockSparseTensor.

This function assumes that there is one block per row/column, otherwise it fails. This assumption makes it so the result can be computed from the dense svds of seperate blocks.
