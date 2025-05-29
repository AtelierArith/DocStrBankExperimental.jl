```
sumOfSqrDiag(X::AnyMatrix)
```

**エイリアス**: `ssd`

実数または複素数の `Matrix`、`Diagonal`、`Hermitian` または `LowerTriangular` 行列 $X$ の対角要素の二乗和。$X$ が長方形の場合（これは `Matrix` 型の場合のみ可能）、主対角線が考慮されます。

**参照**: [AnyMatrix type](@ref)

**関連**: [`sumOfSqr`](@ref), [`sumOfSqrTril`](@ref).

**例**

```julia
using LinearAlgebra, PosDefManifold
X=randn(10, 20)
sumDiag2=sumOfSqrDiag(X) # (1)
sumDiag2=sumOfSqrDiag(𝔻(X)) # (2)
# 𝔻=LinearAlgebra.Diagonal はメインモジュールで宣言されています
```
