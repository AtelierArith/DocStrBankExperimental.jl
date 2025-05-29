```
fcenter(X, v)
fcenter!(X::AbstractMatrix, v)
```

Center each column of a matrix.

  * `X` : Data (n, p).
  * `v` : Centering vector (p).

## examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
xmeans = colmean(X)
fcenter(X, xmeans)
```
