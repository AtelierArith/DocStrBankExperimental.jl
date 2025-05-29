`pca(A, k; [q=10], [exact_svd=false], [s=5])`

Perform fast randomized PCA of a matrix `A` to return `k` first components.

Designed to work with sparse matrices.

# Keyword arguments

  * `exact_svd` - if `true`, use exact SVD on random projections, otherwise use `eig_svd` approximation. Setting it to `true` would improve precision of the algorithm on small eigenvalues, but would drastically decrease performance on large matrices (>1M rows).
  * `q` is the number of pass over `A`, `q` should larger than 1 and `q` times pass eqauls to `(q-2)/2` times power iteration
  * `s` is the excess dimension for the random matrix. This parameter is not supposed to be changed normally.

# Examples

```julia-repl
using SparseArrays
pca(sprand(100, 100, 0.2), 10; q=3)
```
