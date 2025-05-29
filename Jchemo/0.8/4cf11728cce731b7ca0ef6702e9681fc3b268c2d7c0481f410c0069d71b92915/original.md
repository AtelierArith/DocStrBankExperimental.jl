```
fscale(X, v)
fscale!(X::AbstractMatrix, v)
```

Scale each column of a matrix.

  * `X` : Data (n, p).
  * `v` : Scaling vector (p).

## Examples

```julia
using Jchemo

X = rand(5, 2) 
fscale(X, colstd(X))
```
