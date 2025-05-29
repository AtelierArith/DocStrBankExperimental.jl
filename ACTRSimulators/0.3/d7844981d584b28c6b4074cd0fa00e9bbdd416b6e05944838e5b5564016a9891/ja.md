```
ACTRScheduler <: AbstractScheduler
```

ACT-Rイベントスケジューラオブジェクト。

# フィールド

  * `events`: イベントの優先度キュー
  * `time`: システムの現在の時間
  * `running`: trueの場合、シミュレーションを実行できる
  * `model_trace`: trueの場合、モデルイベントを出力する
  * `task_trace`: trueの場合、タスクイベントを出力する
  * `store`: trueの場合、完了したイベントのベクトルを保存する
  * `complete_events`: 完了したイベントのオプションのベクトル
