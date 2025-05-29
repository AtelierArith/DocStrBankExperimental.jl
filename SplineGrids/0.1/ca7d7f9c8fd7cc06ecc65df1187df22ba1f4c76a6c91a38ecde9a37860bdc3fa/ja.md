```
insert_knot(
knot_vector::KnotVector, 
knot_new::AbstractFloat)::Tuple{KnotVector, Integer}
```

新しい重複度1のノットを持つ新しいノットベクトルを作成します。

## 入力

  * `knot_vector`: ノットが追加されるノットベクトルオブジェクト
  * `knot_new`: 新しいノットの値。既存のノット値の一部であってはならない

## 出力

  * `knot_vector_new`: 追加されたノットを持つ新しく作成されたノットベクトル
  * `knot_span_index`: `knots_all[knot_span_index] ≤ knot_new < knots_all[knot_span_index + 1]` となるインデックス
