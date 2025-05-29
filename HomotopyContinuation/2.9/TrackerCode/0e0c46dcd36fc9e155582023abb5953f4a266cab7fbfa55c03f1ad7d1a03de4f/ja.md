```
TrackerCode
```

`CoreTracker` が持つ可能な状態は `TrackerCode.codes` 型であり、次のようになります。

  * `TrackerCode.success`: トラッキングが成功したことを示します。
  * `TrackerCode.tracking`: トラッキングがまだ進行中です。
  * `TrackerCode.terminated_accuracy_limit`: 精度が不十分だったため、トラッキングが終了しました。
  * `TrackerCode.terminated_invalid_startvalue`: 提供された開始値が無効だったため、トラッキングが終了しました。
  * `TrackerCode.terminated_ill_conditioned`: パスが不適切だったため、トラッキングが終了しました。
  * `TrackerCode.terminated_max_steps`: 最大ステップ数に達したため、トラッキングが終了しました。
  * `TrackerCode.terminated_step_size_too_small`: ステップサイズが小さすぎたため、トラッキングが終了しました。
  * `TrackerCode.terminated_unknown`: 意図しないエラーが発生しました。問題を報告することを検討してください。
