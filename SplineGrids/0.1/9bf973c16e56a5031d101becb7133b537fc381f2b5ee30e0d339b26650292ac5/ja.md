```
RefinementMatrix(
    spline_dimension::SplineDimension{Tv, Ti},
    knot_span_index::Integer,
    knot_new
    )::RefinementMatrix{Tv, Ti} where {Tv, Ti <: Integer}
```

ノットベクトルと追加される新しいノットに基づいて、行ごとにリファインメントマトリックスを構築します。

## 入力

  * `spline_dimension`: 新しいノットが追加されるスプライン次元のノットベクトル
  * `knot_span_index`: `knots_all[knot_span_index] ≤ knot_new < knots_all[knot_span_index + 1]` となるインデックス
  * `knot_new`: 新しいノットの値
