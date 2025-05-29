```
aws_event_stream_channel_handler_write_message(handler, message, on_message_written, user_data)
```

チャンネルに[`aws_event_stream_message`](@ref)()を書き込みます。チャンネルがフラッシュされるか、エラーが発生すると、on*message*writtenが呼び出されます。コールバックが呼び出されるまで、messageは有効であり続ける必要があります。エラーが発生した場合、チャンネルは自動的にシャットダウンされます。

### プロトタイプ

```c
int aws_event_stream_channel_handler_write_message( struct aws_channel_handler *handler, struct aws_event_stream_message *message, aws_event_stream_channel_handler_on_message_written_fn *on_message_written, void *user_data);
```
