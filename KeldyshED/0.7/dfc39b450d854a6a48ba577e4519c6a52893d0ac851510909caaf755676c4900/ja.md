```julia
c_matrix(
    ed::KeldyshED.EDCore,
    indices::Vector{Union{Int64, String}},
    sp_index::Int64
) -> Matrix{ScalarType} where ScalarType<:Number

```

正確対角化ソルバーから消滅演算子の非零行列ブロックを抽出します。ブロックはハミルトニアンの固有基底で書かれています。

## 引数

  * `ed`:       正確対角化ソルバーオブジェクト。
  * `indices`:  消滅演算子の複合インデックス（`ed.full_hs.soi`の一部である必要があります）。
  * `sp_index`: 初期部分空間インデックス。

最終的な部分空間インデックスは、ペア（`indices`、`sp_index`）によって一意に決定されます。このペアごとに非零行列は最大で1つです。
