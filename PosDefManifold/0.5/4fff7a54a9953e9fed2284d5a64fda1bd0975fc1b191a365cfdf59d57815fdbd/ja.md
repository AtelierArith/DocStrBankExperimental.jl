```
function typeofVector(
array::Union{AnyMatrix, AnyMatrixVector, AnyMatrixVector₂})
```

**エイリアス**: `typeofVec`

ベクトルの型を返します。型は `HermitianVector`、`DiagonalVector`、`LowerTriangularVector`、または `MatrixVector` のいずれかです。これらのエイリアスはそれぞれ `ℍVector`、`𝔻Vector`、`𝕃Vector`、および `𝕄Vector` です。引数 `array` はこれらの型のいずれかのベクトルである可能性がありますが、次のいずれかでもあります：

`ℍ`、`𝔻`、`𝕃`、および `𝕄`、`ℍVector₂`、`𝔻Vector₂`、`𝕃Vector₂`、`𝕄Vector₂`。

シンボル `ℍ`、`𝔻`、`𝕃`、および `𝕄` のエイリアスについては、[aliases](@ref) を参照してください。最後の4つは [Array of Matrices types](@ref) です。

この関数は、`array` が `ℍVector`、`𝔻Vector`、`𝕃Vector`、または `𝕄Vector` 型でない場合でもベクトル型を返す点で、Julia の関数 [typeof](https://docs.julialang.org/en/v1/base/base/#Core.typeof) とは異なることに注意してください。

**例**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3, 4) # 4つの3x3エルミート行列を生成
typeofMatrix(P) # `Array{Hermitian,1}` を返す
typeof(P) # `Array{Hermitian,1}` も返す

typeofMatrix(P[1]) # `Array{Hermitian,1}` を返す
typeof(P[1]) # `Hermitian{Float64,Array{Float64,2}}` を返す
```
