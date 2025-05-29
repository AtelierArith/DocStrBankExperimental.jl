```
aws_event_loop_schedule_task_now(event_loop, task)
```

イベントループはタスクをスケジュールし、可能な限り早くイベントループスレッドで実行します。キャンセルされたタスクはイベントループスレッドの外で実行される可能性があることに注意してください。この関数は、イベントループスレッドの外部または内部から呼び出すことができます。

タスクの関数が実行されるまで、タスクはクリーンアップまたは変更されるべきではありません。

### プロトタイプ

```c
void aws_event_loop_schedule_task_now(struct aws_event_loop *event_loop, struct aws_task *task);
```
