```
fweight(X, v)
fweight!(X::AbstractMatrix, v)
```

Weight each row of a matrix.

  * `X` : Data (n, p).
  * `v` : A weighting vector (n).

## Examples

```julia
using Jchemo, LinearAlgebra

X = rand(5, 2) 
w = rand(5) 
fweight(X, w)
diagm(w) * X

fweight!(X, w)
X
```
