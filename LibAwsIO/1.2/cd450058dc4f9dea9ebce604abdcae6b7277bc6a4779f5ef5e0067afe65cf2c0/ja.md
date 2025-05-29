```
aws_channel_schedule_task_now_serialized(channel, task)
```

タスクをイベントループ上でできるだけ早く実行するようにスケジュールします。

このバリアントは、常にクロススレッドキューを使用し、すでに宛先イベントループにいる場合に条件付きでスキップすることはありません。「最適」ではありませんが、これにより、タスクがどこから提出されたかに関係なく、タスクの実行を直列化できます。クリティカルセクションからタスクを提出している場合、提出した直列化された順序は、イベントループ上で実行される順序が保証されます。

タスクは、その関数が実行されるまでクリーンアップまたは変更されるべきではありません。

### プロトタイプ

```c
void aws_channel_schedule_task_now_serialized(struct aws_channel *channel, struct aws_channel_task *task);
```
