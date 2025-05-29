```
LocallyRefinedControlPoints(
    control_points_base,
    control_points_refined,
    local_refinements)
```

複数のリファインメントステップを実行し、その過程で制御点の値を上書きするために必要なすべてのデータを提供し、切り捨てられた階層基底（THB）スプラインを生成します。

## フィールド

  * `control_points_base`: 階層の基礎となる密に定義された制御点
  * `control_points_refined`: ローカルリファインメントを適用した後の中間および最終的な制御点配列
  * `local_refinements`: 階層内の各ステップに対するローカルリファインメントのデータ
