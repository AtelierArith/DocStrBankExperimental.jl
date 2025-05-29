```
aws_socket_write(socket, cursor, written_fn, user_data)
```

ソケットに書き込みます。この呼び出しはノンブロッキングであり、可能な限り多くのデータを書き込もうとしますが、残りのデータは利用可能なときに書き込みのためにキューに入れます。written_fnは、カーソル全体が書き込まれたとき、または書き込みが失敗したりキャンセルされたときに呼び出されます。

注意！この関数は[`aws_socket_assign_to_event_loop`](@ref)で使用されるイベントループから呼び出す必要があります。

クライアントソケットの場合、connect()と[`aws_socket_assign_to_event_loop`](@ref)()は、この関数を呼び出す前に呼び出す必要があります。

リスナーからの受信ソケットの場合、最初に[`aws_socket_assign_to_event_loop`](@ref)()を呼び出す必要があります。

### プロトタイプ

```c
int aws_socket_write( struct aws_socket *socket, const struct aws_byte_cursor *cursor, aws_socket_on_write_completed_fn *written_fn, void *user_data);
```
