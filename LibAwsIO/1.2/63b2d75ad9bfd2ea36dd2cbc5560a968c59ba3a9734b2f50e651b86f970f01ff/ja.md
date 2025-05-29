```
aws_event_loop_cancel_task(event_loop, task)
```

タスクをキャンセルします。この関数はイベントループのスレッドから呼び出す必要があり、イベントループのスレッド内からスケジュールされたタスクに対してのみ正しく動作することが保証されています。この呼び出し内でタスクは AWS*TASK*STATUS_CANCELED ステータスで実行されます。

### プロトタイプ

```c
void aws_event_loop_cancel_task(struct aws_event_loop *event_loop, struct aws_task *task);
```
