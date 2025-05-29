```
insert_knot(
    spline_grid::A,
    dim_refinement::Integer,
    knot_new::AbstractFloat;
    evaluate_spline_dimension::Bool = true)::Tuple{A, RefinementMatrix} where {A <: AbstractSplineGrid}
```

指定されたスプライン次元に基づくノットベクトルに新しいノットを追加する新しいスプライングリッドを作成します。

## 入力

  * `spline_grid`: 新しいノットが追加されるスプライングリッド
  * `knot_new`: 追加されるノットの値
  * `dim_refinement`: ノットが追加されるスプライン次元のインデックス
  * `evaluate_spline_dimension`: ノットが追加されるスプライン次元を評価するかどうか。デフォルトは `true`。

## 出力

  * `spline_grid_new`: 更新されたノットベクトルと制御点を除いて、すべて同じ基盤メモリを持つ新しく作成されたスプライングリッド。
  * `refinement_matrix`: ノット挿入次元のノット挿入前の基底関数をノット挿入後の基底関数で表現する疎行列。
