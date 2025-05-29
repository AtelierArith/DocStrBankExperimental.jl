```
aws_socket_read(socket, buffer, amount_read)
```

ソケットから読み取ります。この呼び出しはノンブロッキングであり、データが利用可能でない場合は `AWS_IO_SOCKET_READ_WOULD_BLOCK` を返します。`read` は `buffer` に読み込まれたデータの量です。

`buffer->len` から `buffer->capacity` までの残りのスペースを埋めるのに十分な量を読み取ろうとします。`buffer->len` はバッファの新しい長さを反映するように更新されます。

ソケットが読み取り可能になるときの通知を受け取るには [`aws_socket_subscribe_to_readable_events`](@ref)() を使用してください。

注意！この関数は [`aws_socket_assign_to_event_loop`](@ref) で使用されるイベントループから呼び出す必要があります。

### プロトタイプ

```c
int aws_socket_read(struct aws_socket *socket, struct aws_byte_buf *buffer, size_t *amount_read);
```
