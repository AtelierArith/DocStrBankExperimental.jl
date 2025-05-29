```
gram_schmidt(A::AbstractMatrix,args...) -> AbstractMatrix
gram_schmidt(A::AbstractMatrix,X::AbstractSparseMatrix,args...) -> AbstractMatrix
```

Gram-Schmidt orthogonalization for a matrix `A` under a Euclidean norm. A (positive definite) sparse matrix `X` representing an inner product on the row space of `A` can be provided to make the result orthogonal under a different norm
