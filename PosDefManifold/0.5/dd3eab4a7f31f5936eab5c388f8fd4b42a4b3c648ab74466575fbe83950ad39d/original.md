```
function typeofMatrix(
array::Union{AnyMatrix, AnyMatrixVector, AnyMatrixVector₂})
```

**alias**: `typeofMat`

Return the type of a matrix, either `Hermitian`,  `Diagonal`, `LowerTriangular`, or `Matrix`.  Argument `array` may be a matrix of one of these types, but also one of the following:

`ℍVector`, `ℍVector₂`, `𝔻Vector`, `𝔻Vector₂`, `𝕃Vector`, `𝕃Vector₂`,  `𝕄Vector`, `𝕄Vector₂`.

Those are [Array of Matrices types](@ref).  See also [aliases](@ref) for the symbols `ℍ`, `𝔻`, `𝕃` and `𝕄`.

Note that this function is different from Julia function  [typeof](https://docs.julialang.org/en/v1/base/base/#Core.typeof),  which returns the concrete type (see example below), thus  cannot be used for [typecasting matrices](@ref).

**Examples**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3) # generate a 3x3 Hermitian matrix
typeofMatrix(P) # returns `Hermitian`
typeof(P) # returns `Hermitian{Float64,Array{Float64,2}}`
# typecast P as a `Matrix` M
M=Matrix(P)
# typecast M as a matrix of the same type as P and write the result in A
A=typeofMatrix(P)(M)

Pset=randP(3, 4) # generate a set of 4 3x3 Hermitian matrix
# Pset is an ℍVector type
typeofMatrix(Pset) # again returns `Hermitian`
```
