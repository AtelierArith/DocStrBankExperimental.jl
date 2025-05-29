```
rownorm(X)
```

Compute row-wise norms of a matrix.

  * `X` : Data (n, p).

The norm computed for a row x of `X` is:

  * sqrt(x' * x)

Return a vector.

Note: Thanks to @mcabbott  at https://discourse.julialang.org/t/orders-of-magnitude-runtime-difference-in-row-wise-norm/96363.

## Examples

```julia
using Jchemo

n, p = 5, 6
X = rand(n, p)

rownorm(X)
```
