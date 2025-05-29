```julia
monomial_connection(
    ed::KeldyshED.EDCore,
    mon::KeldyshED.Operators.Monomial
) -> BitMatrix

```

モノミアル演算子（標準演算子 $c$/$c^\dagger$ の積）によって生成される部分空間間の接続の行列を、厳密対角化ソルバーから抽出します。このメソッドは、`length(ed.subspaces)` のサイズを持つ正方形のブール行列を返し、`true` 要素は部分空間間の既存の接続に対応します。

## 引数

  * `ed`: 厳密対角化ソルバーオブジェクト。
  * `mon`: 問題のモノミアル。
