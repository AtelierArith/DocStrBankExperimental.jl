```
sparse_from_full(matrix::Matrix{Int}; [p::Int=0])
```

Create sparse matrix from full integer matrix. If the optional argument `p` is specified and positive, then the returned matrix is an integer matrix which is interpreted over `GF(p)`. On the other hand, if `p` is omitted or equal to zero, then the return matrix has rational type.
