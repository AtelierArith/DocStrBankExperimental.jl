```
colmean(X)
colmean(X, weights::Weight)
```

Compute column-wise means of a matrix.

  * `X` : Data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Return a vector.

## Examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
w = mweight(rand(n))

colmean(X)
colmean(X, w)
```
