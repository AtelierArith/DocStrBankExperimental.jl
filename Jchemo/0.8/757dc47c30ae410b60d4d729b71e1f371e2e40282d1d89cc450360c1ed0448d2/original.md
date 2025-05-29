```
mahsqchol(X, Y)
mahsqchol(X, Y, Uinv)
```

Compute the squared Mahalanobis distances (with a Cholesky factorization) between the observations (rows) of `X` and `Y`.

  * `X` : Data (n, p).
  * `Y` : Data (m, p).
  * `Uinv` : Inverse of the upper matrix of a Cholesky factorization    of a covariance matrix S.   If not given, the factorization is done on S,    the uncorrected covariance matrix of `X`.

When `X` and `Y` are (n, p) and (m, p), repectively, it returns  an object (n, m) with:

  * i, j = distance between row i of `X` and row j of `Y`.

## Examples

```julia
using LinearAlgebra, StatsBase

X = rand(5, 3)
Y = rand(2, 3)

mahsqchol(X, Y)

S = cov(X, corrected = false)
U = cholesky(Hermitian(S)).U 
Uinv = inv(U)
mahsqchol(X, Y, Uinv)

mahsqchol(X[:, 1], 4)
mahsqchol(1, 4, sqrt(2.1))
```
