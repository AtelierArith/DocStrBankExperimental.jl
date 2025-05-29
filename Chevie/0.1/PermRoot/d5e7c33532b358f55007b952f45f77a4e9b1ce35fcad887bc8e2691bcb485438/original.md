`reflectionMatrix(r, ζ=-1)`

returns the matrix of the unitary complex reflection determined by the root `r` and the eigenvalue `ζ`, that is, when the vector space and its dual are identified  via the scalar product `<x,y>=transpose(x)*conj(y)`; the coroot `rᵛ` is then equal to the linear form `x->(1-ζ)<x,r>/<r,r>`.

```julia-repl
julia> reflectionMatrix([1,0,-E(3,2)])
3×3 Matrix{Cyc{Rational{Int64}}}:
  0  0  ζ₃²
  0  1    0
 ζ₃  0    0
```
