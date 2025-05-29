```
aws_event_stream_message_headers(message, headers)
```

メッセージのヘッダーをリストに追加します。各ヘッダーのメモリはメッセージの一部として所有されているため、それを解放したり、そのアドレスを渡したりしないでください。

### プロトタイプ

```c
int aws_event_stream_message_headers( const struct aws_event_stream_message *message, struct aws_array_list *headers);
```
