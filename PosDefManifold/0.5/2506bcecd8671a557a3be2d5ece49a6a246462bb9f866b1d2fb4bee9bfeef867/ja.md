```
(1) 実数または複素数の正定値 `Hermitian` 行列 $P$ が与えられたとき、$LL^H=P$ となる *コレスキー下三角因子* $L$ を返します。$L^H$ または $L$ と $L^H$ の両方を取得するには、代わりに julia 関数 [cholesky](https://bit.ly/2u9Hw5P) を使用してください。

出力として、$L$ は [`LowerTriangular`](https://bit.ly/2U511f3) 型です。

(2) 実数の `Diagonal` 行列 $D$ に対して、$D^{1/2}$ を返します。

**関連情報**: [`choInv`](@ref).

**例**

```

julia using PosDefManifold P=randP(5); L=choL(P); L*L'≈ P ? println(" ⭐ ") : println(" ⛔ ") ```
