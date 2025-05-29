```julia
operator_blocks(
    ed::KeldyshED.EDCore{EDScalarType<:Number},
    op::KeldyshED.Operators.OperatorExpr{OPScalarType<:Number},
    sp_index::Int64
) -> Dict{Int64, Matrix{_A}} where _A

```

与えられた（初期）部分空間で状態に作用する演算子の行列表現のブロックを計算します。計算されたブロックは辞書 `最終部分空間インデックス => 行列` として返され、行列はハミルトニアンの固有基底で書かれています。

## 引数

  * `ed`:       正確対角化ソルバーオブジェクト。
  * `op`:       演算子式。
  * `sp_index`: 初期部分空間インデックス。
