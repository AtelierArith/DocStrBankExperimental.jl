```
schedule_updates(variables...; pipeline_stage = ScheduleOnPipelineStage(PendingScheduler()))
```

指定された変数の後部周辺更新を `stage` を使用してスケジュールします。デフォルトでは、`Rocket.jl` ライブラリの `PendingScheduler()` を使用して `ScheduleOnPipelineStage` を作成します。すべてのスケジュールされた更新を解放するために利用可能な `release!` メソッドを持つスケジューラを返します。
