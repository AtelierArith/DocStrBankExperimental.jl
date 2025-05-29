```
colNorm(X::Union{𝕄{T}, ℍ{T}}, j::Int) where T<:RealOrComplex
```

実数または複素数の `Matrix` または `Hermitian` 行列 $X$ が与えられたとき、$j^{th}$ 列のユークリッドノルムを返します。

この関数は [BLAS.nrm2](https://docs.julialang.org/en/v1/stdlib/LinearAlgebra/#LinearAlgebra.BLAS.nrm2) ルーチンを呼び出します。 [Threads](@ref) を参照してください。

**関連情報**: [`normalizeCol!`](@ref), [`colProd`](@ref), [`sumOfSqr`](@ref).

**例**

```julia
using PosDefManifold
X=randn(10, 20)
normOfSecondColumn=colNorm(X, 2)
```
