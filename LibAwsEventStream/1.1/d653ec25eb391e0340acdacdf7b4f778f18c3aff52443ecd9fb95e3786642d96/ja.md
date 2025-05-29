```
aws_event_stream_message_clean_up(message)
```

内部で割り当てられたメモリをクリーンアップします。aws*aws*event*stream*message*from*buffer関数を使用した場合でも、APIの互換性の理由から、常にこれを呼び出してください。

### プロトタイプ

```c
void aws_event_stream_message_clean_up(struct aws_event_stream_message *message);
```
