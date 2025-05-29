```
testing_channel_drain_queued_tasks(testing)
```

スケジュールされたタスクを繰り返し実行し、未来のタスクのみが残るまで実行します。これは、今のタスクがさらに今のタスクをスケジュールする連鎖反応がある一般的なケースをカバーしています。

### プロトタイプ

```c
static inline void testing_channel_drain_queued_tasks(struct testing_channel *testing);
```
