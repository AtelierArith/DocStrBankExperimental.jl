```
function typeofMatrix(
array::Union{AnyMatrix, AnyMatrixVector, AnyMatrixVector₂})
```

**エイリアス**: `typeofMat`

行列の型を返します。`Hermitian`、`Diagonal`、`LowerTriangular`、または`Matrix`のいずれかです。引数`array`は、これらの型のいずれかの行列である可能性がありますが、次のいずれかでもあります：

`ℍVector`、`ℍVector₂`、`𝔻Vector`、`𝔻Vector₂`、`𝕃Vector`、`𝕃Vector₂`、`𝕄Vector`、`𝕄Vector₂`。

これらは[行列の配列の型](@ref)です。また、記号`ℍ`、`𝔻`、`𝕃`、`𝕄`については、[エイリアス](@ref)も参照してください。

この関数は、具体的な型を返すJuliaの関数[typeof](https://docs.julialang.org/en/v1/base/base/#Core.typeof)とは異なることに注意してください（以下の例を参照）。したがって、[行列の型変換](@ref)には使用できません。

**例**

```julia
using LinearAlgebra, PosDefManifold
P=randP(3) # 3x3のエルミート行列を生成
typeofMatrix(P) # `Hermitian`を返す
typeof(P) # `Hermitian{Float64,Array{Float64,2}}`を返す
# Pを`Matrix` Mとして型変換
M=Matrix(P)
# MをPと同じ型の行列として型変換し、結果をAに書き込む
A=typeofMatrix(P)(M)

Pset=randP(3, 4) # 4つの3x3エルミート行列のセットを生成
# PsetはℍVector型
typeofMatrix(Pset) # 再び`Hermitian`を返す
```
