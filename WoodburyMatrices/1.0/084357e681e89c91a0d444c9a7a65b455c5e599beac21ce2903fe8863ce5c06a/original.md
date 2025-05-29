```
W = SymWoodbury(A, B, D; allocatetmp::Bool=false)
```

Represent a matrix of the form `W = A + BDBᵀ`, where `A` and `D` are symmetric. Equations `Wx = b` will be solved using the [Woodbury matrix identity](https://en.wikipedia.org/wiki/Woodbury_matrix_identity).

If your main goal is to solve equations, it can be advantageous to supply `A` as a factorization (e.g., `SymWoodbury(cholesky(A), B, D)` if `A` is a positive semidefinite matrix).

This checks that `A` is symmetric; you can elide the check by passing a `Symmetric` matrix or factorization.

See also [Woodbury](@ref), where `allocatetmp` is explained.
