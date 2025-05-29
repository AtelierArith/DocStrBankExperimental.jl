API: 

  * `Scheduler`: スケジューラオブジェクト
  * `Event`: イベントオブジェクト
  * `run!`: シミュレーションを実行
  * `remove_event!`: イベントを削除
  * `stop!`: シミュレーションを停止
  * `register!`: イベントをスケジューラに追加
  * `reset!`: スケジューラをリセット
  * `replay_events`: 完了したイベントを出力
  * `when types:` now, at, after, every

詳細についてはヘルプを使用してください。例えば、

```julia
] register!
```
