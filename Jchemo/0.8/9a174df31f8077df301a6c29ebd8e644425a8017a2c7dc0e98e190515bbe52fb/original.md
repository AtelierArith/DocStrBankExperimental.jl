```
fcscale(X, u, v)
fcscale!(X, u, v)
```

Center and fscale each column of a matrix.

  * `X` : Data  (n, p).
  * `u` : Centering vector (p).
  * `v` : Scaling vector (p).

## examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
xmeans = colmean(X)
xscales = colstd(X)
fcscale(X, xmeans, xscales)
```
