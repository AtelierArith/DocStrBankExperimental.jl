```
tpod(red_style::ReductionStyle,A::AbstractMatrix) -> AbstractMatrix
tpod(red_style::ReductionStyle,A::AbstractMatrix,X::AbstractSparseMatrix) -> AbstractMatrix
```

Truncated proper orthogonal decomposition of `A`. When provided, `X` is a (symmetric, positive definite) norm matrix with respect to which the output is made orthogonal. If `X` is not provided, the output is orthogonal with respect to the euclidean norm
