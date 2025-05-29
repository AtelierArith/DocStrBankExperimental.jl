```
(1) pow(P::ℍ{T}, args...) where T<:RealOrComplex
(2) pow(D::𝔻{S}, args...) where S<:Real

(1) 正定半定の `Hermitian` 行列 $P$ が与えられたとき、任意の指数 $r_1, r_2,...$ に対して $P^{r_1}, P^{r_2},...$ を返します。引数として $P$ の後に渡された要素の数と同じ数の要素を含むタプルを返します。

$P$ は `Hermitian` としてフラグ付けされている必要があります。行列の型変換については [typecasting matrices](@ref) を参照してください。

$arg1, arg2,...$ は実数です。

実数の `Diagonal` 行列に対しては特別なメソッドが提供されています (2)。

**関連情報**: [`invsqrt`](@ref).

**例**

```

julia using LinearAlgebra, PosDefManifold P=randP(5);     # Hermitian 行列を生成するには P=randP(ComplexF64, 5) を使用 Q=pow(P, 0.5);            # =>  QQ=P Q, W=pow(P, 0.5, -0.5); W*P*W ≈ I ? println(" ⭐ ") : println(" ⛔ ") Q*Q ≈ P ? println(" ⭐ ") : println(" ⛔ ") R, S=pow(P, 0.3, 0.7); R*S ≈ P ? println(" ⭐ ") : println(" ⛔ ") ```
