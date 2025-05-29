```julia
operator_blocks(
    ed::KeldyshED.EDCore{EDScalarType<:Number},
    op::KeldyshED.Operators.OperatorExpr{OPScalarType<:Number}
) -> Dict{Tuple{Int64, Int64}, Matrix{_A}} where _A

```

演算子の行列表現のブロックを計算します。

計算されたブロックは辞書として返されます `(初期サブスペースインデックス, 最終サブスペースインデックス) => 行列` であり、行列はハミルトニアンの固有基底で表現されます。

## 引数

  * `ed`:       正確対角化ソルバーオブジェクト。
  * `op`:       演算子式。
