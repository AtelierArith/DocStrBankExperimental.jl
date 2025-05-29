```
colnorm(X)
colnorm(X, weights::Weight)
```

Compute column-wise norms of a matrix.

  * `X` : Data (n, p).
  * `weights` : Weights (n) of the observations.    Must be of type `Weight` (see e.g. function `mweight`).

The norm computed for a column x of `X` is:

  * sqrt(x' * x)

The weighted norm is:

  * sqrt(x' * D * x), where D is the diagonal matrix of `weights.w`

**Warning:** `colnorm(X, mweight(ones(n)))` = `colnorm(X) / sqrt(n)`.

Return a vector.

## Examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
w = mweight(rand(n))

colnorm(X)
colnorm(X, w)
```
