```
(1) tr(P::ℍ{T}, Q::ℍ{T})
(2) tr(P::ℍ{T}, M::𝕄{T})
(3) tr(D::𝔻{T}, H::Union{ℍ{T}, 𝕄{T}})
(4) tr(H::Union{ℍ{T}, 𝕄{T}}, D::𝔻{T})
上記すべてについて: ここで T<:RealOrComplex

(1) 2つの `Hermitian` 正定値行列 $P$ と $Q$ が与えられた場合、積 $PQ$ のトレースを返します。これは、$P$ と $Q$ が複素数であっても実数です。

$P$ は常に `Hermitian` としてフラグ付けされる必要があります。行列の型変換については [typecasting matrices](@ref) を参照してください。

(2) $Q$ が `Matrix` オブジェクトである場合、次のように返します。

  * 積 $PQ$ が実数であるか、すべての固有値が正の実数である場合は実数のトレース。
  * 積 $PQ$ が実数でなく、複素数の固有値を持つ場合は複素数のトレース。

メソッド (3) と (4) は、$D$ が `Diagonal` 行列で、$H$ が $Hermitian$ または $Matrix$ オブジェクトである場合、積 $DH$ または $HD$ のトレースを返します。結果は入力行列と同じ型になります。

すべてのメソッドにおいて、すべての引数は同じ型でなければなりません。

## 数学

$P$ と $Q$ を `Hermitian` 行列とし、トレースの性質（例えば、循環性と類似不変性）を使用して、この関数を使用していくつかの式のトレースを迅速に計算できます。例えば：

$\textrm{tr}(PQ)=\textrm{tr}(P^{1/2}QP^{1/2})$

および

$\textrm{tr}(PQP)=\textrm{tr}(P^{2}Q)$ （以下の例を参照）。

**参照**: [trace](https://bit.ly/2HoOLiM)。

**関連**: [`DiagOfProd`](@ref), [`tr1`](@ref)。

**例**

```

julia using PosDefManifold P=randP(ComplexF64, 5) # ランダムな複素正定値行列 5x5 を生成 Q=randP(ComplexF64, 5) # ランダムな複素正定値行列 5x5 を生成 tr(P, Q) ≈ tr(P*Q) ? println(" ⭐ ") : println(" ⛔ ") tr(P, Q) ≈ tr(sqrt(P)*Q*sqrt(P)) ? println(" ⭐ ") : println(" ⛔ ") tr(sqr(P), Q) ≈ tr(P*Q*P) ? println(" ⭐ ") : println(" ⛔ ") ```
