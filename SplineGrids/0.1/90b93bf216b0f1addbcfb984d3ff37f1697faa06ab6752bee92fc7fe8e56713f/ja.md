```
error_informed_local_refinement!(
    spline_grid::AbstractSplineGrid{Nin, Nout, HasWeights, Tv, Ti},
    error::AbstractArray;
    threshold_factor::Number = 1.0
    )::Nothing where {Nin, Nout, HasWeights, Tv, Ti}
```

`error` 配列に基づいて、`spline_grid.eval` と同じ形状を持つローカルに細分化されたスプライングリッドの最終レベルを細分化します。これは以下の手順で行われます：

  * 精緻化行列の乗算の随伴を使用して、エラーを制御点にマッピングします
  * 出力次元にわたって合計し、`control_grid_error` に格納された各制御点ごとに単一の数値を取得します
  * 値が `threshold = threshold_factor * mean(control_grid_error)` より大きい各制御点をアクティブにします
