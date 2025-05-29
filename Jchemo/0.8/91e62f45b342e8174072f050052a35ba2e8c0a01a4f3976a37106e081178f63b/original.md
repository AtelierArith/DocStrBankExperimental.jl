```
colsum(X)
colsum(X, weights::Weight)
```

Compute column-wise sums of a matrix.

  * `X` : Data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

Return a vector.

## Examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
w = mweight(rand(n))

colsum(X)
colsum(X, w)
```
