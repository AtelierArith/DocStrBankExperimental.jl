```julia
c_connection(
    ed::KeldyshED.EDCore,
    indices::Vector{Union{Int64, String}}
) -> BitMatrix

```

アニヒレーション演算子によって生成されたサブスペース間の接続の行列を、厳密対角化ソルバーから抽出します。このメソッドは、`length(ed.subspaces)` のサイズを持つ正方形のブール行列を返し、`true` の要素はサブスペース間の既存の接続に対応します。

## 引数

  * `ed`:       厳密対角化ソルバーオブジェクト。
  * `indices`:  アニヒレーション演算子の複合インデックス（`ed.full_hs.soi` の一部である必要があります）。
