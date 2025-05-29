```
(1) sqr(P::ℍ{T}) where T<:RealOrComplex
(2) sqr(X::Union{𝕄{T}, 𝕃{T}, 𝔻{S}}) where T<:RealOrComplex where S<:Real

(1) 正定半定の `Hermitian` 行列 $P$ が与えられたとき、その平方 $P^{2}$ を計算します。

$P$ は Hermitian としてフラグ付けされている必要があります。行列の型変換については [typecasting matrices](@ref) を参照してください。

`Matrix` 型の一般的な行列、`LowerTriangular` 行列、および実数の `Diagonal` 行列 (2) に対してもメソッドが提供されています。出力は入力と同じ型になります。

**関連情報**: [`pow`](@ref).

**例**

```

julia using PosDefManifold P=randP(5); P²=sqr(P);  # =>  P²=PP sqrt(P²)≈ P ? println(" ⭐ ") : println(" ⛔ ") ```
