```julia
monomial_matrix(
    ed::KeldyshED.EDCore{ScalarType<:Number},
    mon::KeldyshED.Operators.Monomial,
    sp_index::Int64
) -> Any

```

モノミアル演算子（正準演算子 $c$/$c^\dagger$ の積）から非零行列ブロックを抽出します。ブロックはハミルトニアンの固有基底で書かれています。

## 引数

  * `ed`:       正確対角化ソルバーオブジェクト。
  * `mon`:      問題のモノミアル。
  * `sp_index`: 初期部分空間インデックス。

最終的な部分空間インデックスは、ペア（`mon`、`sp_index`）によって一意に決定されます。このペアごとに非零行列は最大で1つしか存在しません。
