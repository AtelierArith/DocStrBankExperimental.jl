```
sumOfSqrTril(X::AnyMatrix, k::Int=0)
```

**alias**: `sst`

Given a real or complex `Matrix`, `Diagonal`, `Hermitian` or  `LowerTriangular` matrix $X$ (see [AnyMatrix type](@ref)),  return the sum of squares of the elements  in its lower triangle up to the $k^{th}$ underdiagonal.

`Matrix` $X$ may be rectangular.

$k$ must be in range

  * `1-size(X, 1):c-1` for $X$ `Matrix`, `Diagonal` or `Hermitian`,
  * `1-size(X, 1):0` for $X$ `LowerTriangular`.

For $X$ `Diagonal` the result is

  * $0$ if $k<0$,
  * the sum of the squares of the diagonal elements otherwise.

See julia [tril(M, k::Integer)](https://bit.ly/2Tbx8o7) function  for numbering of diagonals.

**See also**: [`sumOfSqr`](@ref), [`sumOfSqrDiag`](@ref).

**Examples**

```julia
using PosDefManifold
A=[4. 3.; 2. 5.; 1. 2.]
#3×2 Array{Float64,2}:
# 4.0  3.0
# 2.0  5.0
# 1.0  2.0

s=sumOfSqrTril(A, -1)
# 9.0 = 1²+2²+2²

s=sumOfSqrTril(A, 0)
# 50.0 = 1²+2²+2²+4²+5²
```
