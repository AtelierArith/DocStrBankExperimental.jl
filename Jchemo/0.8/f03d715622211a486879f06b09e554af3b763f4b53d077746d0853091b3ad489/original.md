```
mahsq(X, Y)
mahsq(X, Y, Sinv)
```

Squared Mahalanobis distances between      the rows of `X` and `Y`.

  * `X` : Data (n, p).
  * `Y` : Data (m, p).
  * `Sinv` : Inverse of a covariance matrix S.   If not given, S is computed as the uncorrected    covariance matrix of `X`.

When `X` and `Y` are (n, p) and (m, p), repectively, it returns  an object (n, m) with:

  * i, j = distance between row i of `X` and row j of `Y`.

## Examples

```julia
using StatsBase 

X = rand(5, 3)
Y = rand(2, 3)

mahsq(X, Y)

S = cov(X, corrected = false)
Sinv = inv(S)
mahsq(X, Y, Sinv)
mahsq(X[1:1, :], Y[1:1, :], Sinv)

mahsq(X[:, 1], 4)
mahsq(1, 4, 2.1)
```
