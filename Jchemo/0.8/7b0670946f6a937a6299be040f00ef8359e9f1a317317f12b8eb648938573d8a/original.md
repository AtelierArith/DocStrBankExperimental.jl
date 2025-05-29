```
rowmean(X)
```

Compute row-wise means of a matrix.

  * `X` : Data (n, p).

Return a vector.

## Examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)
rowmean(X)
```
