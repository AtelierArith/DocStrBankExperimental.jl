```julia
cdag_connection(
    ed::KeldyshED.EDCore,
    op_linear_index::Int64
) -> BitMatrix

```

生成された生成演算子によるサブスペース間の接続の行列を抽出します。このメソッドは、`length(ed.subspaces)`のサイズを持つ正方形のブール行列を返し、`true`の要素はサブスペース間の既存の接続に対応します。

## 引数

  * `ed`:              正確対角化ソルバーオブジェクト。
  * `op_linear_index`: `ed.full_hs.soi`によって定義された生成演算子の線形インデックス。
