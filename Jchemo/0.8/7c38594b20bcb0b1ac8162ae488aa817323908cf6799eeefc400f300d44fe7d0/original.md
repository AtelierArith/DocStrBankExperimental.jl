```
rowvar(X)
```

Compute row-wise variances (uncorrected) of a matrix.

  * `X` : Data (n, p).

Return a vector.

## Examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
rowvar(X)
```
