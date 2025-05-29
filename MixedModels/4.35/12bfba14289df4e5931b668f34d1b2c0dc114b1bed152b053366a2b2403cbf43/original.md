```
sparseL(m::LinearMixedModel; fname::Symbol=first(fnames(m)), full::Bool=false)
```

Return the lower Cholesky factor `L` as a `SparseMatrix{T,Int32}`.

`full` indicates whether the parts of `L` associated with the fixed-effects and response are to be included.

`fname` specifies the first grouping factor to include. Blocks to the left of the block corresponding  to `fname` are dropped. The default is the first, i.e., leftmost block and hence all blocks.
