```
aws_channel_schedule_task_future(channel, task, run_at_nanos)
```

指定された時間にイベントループでタスクを実行するようにスケジュールします。これは、タスクを正しいスレッドに移動させるための理想的な方法です。また、コンテキストスイッチにも便利です。現在の時間をナノ秒単位で取得するには、[`aws_channel_current_clock_time`](@ref)()を使用してください。この関数は、任意のスレッドから呼び出すことが安全です。

タスクは、その関数が実行されるまでクリーンアップまたは変更してはいけません。

### プロトタイプ

```c
void aws_channel_schedule_task_future( struct aws_channel *channel, struct aws_channel_task *task, uint64_t run_at_nanos);
```
