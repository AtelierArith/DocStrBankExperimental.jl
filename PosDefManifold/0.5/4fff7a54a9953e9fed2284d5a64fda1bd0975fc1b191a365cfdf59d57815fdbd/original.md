```
function typeofVector(
array::Union{AnyMatrix, AnyMatrixVector, AnyMatrixVector₂})
```

**alias**: `typeofVec`

Return the type of a Vector, either `HermitianVector`,  `DiagonalVector`, `LowerTriangularVector`, or `MatrixVector`.  The aliases of those are, respectvely, `ℍVector`, `𝔻Vector`, `𝕃Vector` and  `𝕄Vector`.  Argument `array` may be a vector of one of these types, but also one of the  following:

`ℍ`, `𝔻`, `𝕃` and `𝕄`, `ℍVector₂`, `𝔻Vector₂`, `𝕃Vector₂`, `𝕄Vector₂`.

See [aliases](@ref) for the symbols `ℍ`, `𝔻`, `𝕃` and `𝕄`.  The last four are [Array of Matrices types](@ref).

Note that this function is different from Julia function  [typeof](https://docs.julialang.org/en/v1/base/base/#Core.typeof)  only in that it returns the vector type also if `array`  is not of the `ℍVector`, `𝔻Vector`, `𝕃Vector` or  `𝕄Vector` type.

**Examples**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3, 4) # generate 4 3x3 Hermitian matrix
typeofMatrix(P) # returns `Array{Hermitian,1}`
typeof(P) # also returns `Array{Hermitian,1}`

typeofMatrix(P[1]) # returns `Array{Hermitian,1}`
typeof(P[1]) # returns `Hermitian{Float64,Array{Float64,2}}`
```
