```
(1) colProd(X::Union{𝕄{T}, ℍ{T}}, j::Int, l::Int)
(2) colProd(X::Union{𝕄{T}, ℍ{T}}, Y::Union{𝕄{T}, ℍ{T}}, j::Int, l::Int)
for all above: where T<:RealOrComplex

(1) 実数または複素数の `Matrix` または `Hermitian` 行列 $X$ が与えられたとき、$j^{th}$ 列と $l^{th}$ 列のドット積を返します。これは次のように定義されます。

$\sum_{i=1}^{r} \big(x_{ij}^*x_{il}\big),$

ここで、$r$ は $X$ の行数であり、$^*$ は複素共役を示します（行列が実数の場合は何もありません）。

(2) 実数または複素数の `Matrix` または `Hermitian` 行列 $X$ と $Y$ が与えられたとき、$X$ の $j^{th}$ 列と $Y$ の $l^{th}$ 列のドット積を返します。これは次のように定義されます。

$\sum_{i=1}^{r} \big(x_{ij}^*y_{il}\big),$

ここで、$r$ は $X$ と $Y$ の行数であり、$^*$ は上記の通りです。

!!! note "Nota Bene"
    $X$ と $Y$ は異なる列数を持つことがありますが、行数は同じでなければなりません。

引数 $j$ と $l$ は次の範囲の正の整数でなければなりません。

  * (1) `j,l in 1:size(X, 2)`,
  * (2) `j in 1:size(X, 2), l in 1:size(Y, 2)`.

**See also**: [`normalizeCol!`](@ref), [`colNorm`](@ref).

**Examples**

```

julia using PosDefManifold X=randn(10, 20) p=colProd(X, 1, 3) Y=randn(10, 30) q=colProd(X, Y, 2, 25) ```
