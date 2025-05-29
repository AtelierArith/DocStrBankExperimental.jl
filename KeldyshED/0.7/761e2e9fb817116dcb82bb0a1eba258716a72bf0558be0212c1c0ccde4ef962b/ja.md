```julia
cdag_connection(
    ed::KeldyshED.EDCore,
    indices::Vector{Union{Int64, String}}
) -> BitMatrix

```

生成された創造演算子によるサブスペース間の接続の行列を抽出します。このメソッドは、`length(ed.subspaces)`のサイズを持つ正方形のブール行列を返し、`true`の要素はサブスペース間の既存の接続に対応します。

## 引数

  * `ed`:       正確対角化ソルバーオブジェクト。
  * `indices`:  創造演算子の複合インデックス（`ed.full_hs.soi`の一部である必要があります）。
