```julia
c_matrix(
    ed::KeldyshED.EDCore,
    op_linear_index::Int64,
    sp_index::Int64
) -> Matrix{ScalarType} where ScalarType<:Number

```

正確対角化ソルバーから消滅演算子の非零行列ブロックを抽出します。ブロックはハミルトニアンの固有基底で書かれています。

## 引数

  * `ed`:              正確対角化ソルバーオブジェクト。
  * `op_linear_index`: `ed.full_hs.soi`によって定義された消滅演算子の線形インデックス。
  * `sp_index`:        初期部分空間インデックス。

最終的な部分空間インデックスは、ペア（`op_linear_index`、`sp_index`）によって一意に決定されます。このペアごとに非零行列は最大で1つしか存在しません。
