```
sumOfSqrDiag(X::AnyMatrix)
```

**alias**: `ssd`

Sum of squares of the diagonal elements in real or complex `Matrix`,  `Diagonal`, `Hermitian` or `LowerTriangular` matrix $X$.  If $X$ is rectangular (which can be only if it is of the `Matrix` type),  the main diagonal is considered.

**See** [AnyMatrix type](@ref)

**See also**: [`sumOfSqr`](@ref), [`sumOfSqrTril`](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
X=randn(10, 20)
sumDiag2=sumOfSqrDiag(X) # (1)
sumDiag2=sumOfSqrDiag(𝔻(X)) # (2)
# 𝔻=LinearAlgebra.Diagonal is declated in the main module
```
