```
(1) sumOfSqr(A::Array)
(2) sumOfSqr(H::ℍ{T})
(3) sumOfSqr(L::𝕃{T})
(4) sumOfSqr(D::𝔻{T})
(5) sumOfSqr(X::Union{𝕄{T}, ℍ{T}}, j::Int)
(6) sumOfSqr(X::Union{𝕄{T}, ℍ{T}}, range::UnitRange)
(1)-(6)について: ここで T<:RealOrComplex

**エイリアス**: `ss`

返す

  * (1) 任意の次元の配列 $A$ の要素の二乗和。
  * (2) (1)と同様だが、`Hermitian` 行列 $H$ の下三角部分のみを使用。
  * (3) (1)と同様だが、`LowerTriangular` 行列 $L$ の場合。
  * (4) (1)と同様だが、対角行列 $D$ の場合（対角要素の二乗和）。
  * (5) `Matrix` または `Hermitian` $X$ の $j^{th}$ 列の二乗和。
  * (6) 指定された範囲内の `Matrix` または `Hermitian` $X$ の列の二乗和。

すべてのメソッドは実数および複素数行列をサポートします。

メソッド (1) のみが任意の次元の配列に対して機能します。

メソッド (1)-(4) は [フロベニウスノルム](https://bit.ly/2Fi10eH) の二乗を返します。

メソッド (5) では、$j$ は `1:size(X, 1)` の範囲内の正の整数です。

メソッド (6) では、$range$ は [UnitRange 型](https://bit.ly/2HDoFbk) です。

**関連**: [`colNorm`](@ref), [`sumOfSqrDiag`](@ref), [`sumOfSqrTril`](@ref).

**例**

```

julia using PosDefManifold X=randn(10, 20) sum2=sumOfSqr(X)        # (1) すべての要素の二乗和 sum2=sumOfSqr(X, 1)     # (2) 列 1 の要素の二乗和 sum2=sumOfSqr(X, 2:4)   # (3) 列 2 から 4 の要素の二乗和 ```
