Scheduler <: AbstractScheduler

  * `events`: イベントの優先度キュー
  * `time`: システムの現在の時間
  * `running`: true の場合、シミュレーションを実行できる
  * `trace`: true の場合、イベントを出力する
  * `store`: true の場合、完了したイベントのベクターを保存する
  * `complete_events`: 完了したイベントのオプションのベクター
