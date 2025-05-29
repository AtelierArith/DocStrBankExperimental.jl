```
insert_knot(
    spline_dimension::SplineDimension{Tv, Ti},
    knot_new::AbstractFloat;
    recompute_sample_indices::Bool = true,
    evaluate::Bool = true)::Tuple{
        SplineDimension{Tv, Ti},
        RefinementMatrix{Tv, Ti}
    } where {Tv, Ti}
```

新しいノットを重複度1で持つ新しいスプライン次元を作成します。

## 入力

  * `spline_dimension`: 新しいノットが追加されるスプライン次元
  * `knot_new`: 新しいノットの値
  * `recompute_sample_indices`: ノット挿入後にサンプルポイントのインデックスを再計算するかどうか。デフォルトは`true`です。
  * `evaluate`: ノット挿入後にスプライン次元を評価するかどうか。デフォルトは`true`です。

## 出力

  * `spline_dimension_new`: 新しいノットベクトルを除いて同じ基盤メモリを持つ新しく作成されたスプライン次元。
  * `refinement_matrix`: ノット挿入前の基底関数をノット挿入後の基底関数の観点から表現する疎行列。
