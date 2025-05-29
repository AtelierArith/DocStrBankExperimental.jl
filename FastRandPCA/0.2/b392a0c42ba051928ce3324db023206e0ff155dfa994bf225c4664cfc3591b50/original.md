`eig_svd(A, [k]; [kwargs...])`

Perform singular value decomposition of a matrix `A` by estimating `svd(A' * A)`. If `k` is provided, Krylov iterative solver is used to return only `k` largest singular values and corresponding singular vectors.

Designed to work with sparse matrices. Keyword arguments are forwarded to `KrylovKit.svdsolve`.

# Examples

```julia-repl
using SparseArrays
eig_svd(sprand(100, 100, 0.2), 10)
```
