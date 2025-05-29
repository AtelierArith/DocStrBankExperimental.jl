```
getknn(Xtrain, X; metric = :eucl, k = 1)
```

Return the k nearest neighbors in `Xtrain` of each row of the query `X`.

  * `Xtrain` : Training X-data.
  * `X` : Query X-data.

Keyword arguments:

  * `metric` : Type of distance used for the query.    Possible values are `:eucl` (Euclidean),   `:mah` (Mahalanobis), `:sam` (spectral angular distance),   `:cor` (correlation distance).
  * `k` : Number of neighbors to return.

The distances (not squared) are also returned.

Spectral angular and correlation distances between two vectors x and y:

  * Spectral angular distance (x, y) = acos(x'y / normv(x)normv(y)) / pi
  * Correlation distance (x, y) = sqrt((1 - cor(x, y)) / 2)

Both distances are bounded within 0 (y = x) and 1 (y = -x).

## Examples

```julia
using Jchemo
Xtrain = rand(5, 3)
X = rand(2, 3)
x = X[1:1, :]

k = 3
res = getknn(Xtrain, X; k)
res.ind  # indexes
res.d    # distances

res = getknn(Xtrain, x; k)
res.ind

res = getknn(Xtrain, X; metric = :mah, k)
res.ind
```
