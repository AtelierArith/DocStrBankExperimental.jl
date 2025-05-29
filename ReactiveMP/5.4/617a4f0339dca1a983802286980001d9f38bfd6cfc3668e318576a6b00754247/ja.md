```
ScheduleOnPipelineStage{S} <: AbstractPipelineStage
```

`Rocket.jl`ライブラリからの`schedule_on()`オペレーターを指定されたパイプラインに提供された`scheduler`で適用します。

# 引数

  * `scheduler`: 更新をスケジュールするためのスケジューラー。`Rocket.jl`ライブラリおよび`schedule_on()`オペレーターと互換性がある必要があります。
