```
aws_event_loop_schedule_task_future(event_loop, task, run_at_nanos)
```

イベントループはタスクをスケジュールし、指定された時間に実行します。現在の時間をナノ秒単位で照会するには、[`aws_event_loop_current_clock_time`](@ref)()を使用してください。キャンセルされたタスクはイベントループスレッドの外で実行される可能性があることに注意してください。この関数は、イベントループスレッドの外部または内部から呼び出すことができます。

タスクの関数が実行されるまで、タスクはクリーンアップまたは変更されるべきではありません。

### プロトタイプ

```c
void aws_event_loop_schedule_task_future( struct aws_event_loop *event_loop, struct aws_task *task, uint64_t run_at_nanos);
```
