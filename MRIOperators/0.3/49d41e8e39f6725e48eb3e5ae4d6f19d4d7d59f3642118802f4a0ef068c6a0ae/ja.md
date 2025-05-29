```
MapSliceOp(trafo, dim::Int64, size1::Tuple, size2::Tuple; T=ComplexF64)
```

は、配列の次元 `dim` の各スライスに `trafo` を適用する演算子を生成します。

# 引数

  * `trafo`           - 適用する変換
  * `size1`           - 変換される配列のサイズ
  * `size2`           - すべてのスライスに trafo を適用した結果の配列のサイズ
  * (`T=ComplexF64`)  - 変換の型
