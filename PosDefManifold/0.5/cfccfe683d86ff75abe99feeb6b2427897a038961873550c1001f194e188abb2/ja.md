```
sumOfSqrTril(X::AnyMatrix, k::Int=0)
```

**エイリアス**: `sst`

実数または複素数の `Matrix`、`Diagonal`、`Hermitian` または `LowerTriangular` 行列 $X$（[AnyMatrix type](@ref)を参照）に対して、$k^{th}$ 下対角線までの要素の下三角部分の平方和を返します。

`Matrix` $X$ は長方形である可能性があります。

$$
k
$$

は範囲内でなければなりません。

  * `1-size(X, 1):c-1` は $X$ が `Matrix`、`Diagonal` または `Hermitian` の場合、
  * `1-size(X, 1):0` は $X$ が `LowerTriangular` の場合。

$$
X
$$

が `Diagonal` の場合、結果は次のようになります。

  * $$
    k<0
    $$

    の場合は $0$、
  * それ以外の場合は対角要素の平方和。

対角線の番号付けについては、julia の [tril(M, k::Integer)](https://bit.ly/2Tbx8o7) 関数を参照してください。

**関連**: [`sumOfSqr`](@ref)、[`sumOfSqrDiag`](@ref)。

**例**

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
