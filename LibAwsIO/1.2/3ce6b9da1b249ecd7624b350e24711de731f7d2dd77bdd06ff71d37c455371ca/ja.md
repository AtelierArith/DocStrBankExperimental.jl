```
testing_channel_run_currently_queued_tasks(testing)
```

現在スケジュールされているすべてのタスクを実行します。時間が来たタスクのみが対象です。未来のタスクのみが残るまで、[`testing_channel_drain_queued_tasks`](@ref)()を使用してタスクを繰り返し実行します。

### プロトタイプ

```c
static inline void testing_channel_run_currently_queued_tasks(struct testing_channel *testing);
```
