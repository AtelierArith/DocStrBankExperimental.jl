```
aws_socket_handler_new(allocator, socket, slot, max_read_size)
```

ソケットハンドラーは、チャネル内の最初のスロット/ハンドラーであるべきです。これは、読み取りおよび書き込み通知のためにチャネルのイベントループと直接相互作用します。max*read*sizeは、コンテキストスイッチの前にソケットから読み取る最大データ量です（継続タスクがスケジュールされます）。

### プロトタイプ

```c
struct aws_channel_handler *aws_socket_handler_new( struct aws_allocator *allocator, struct aws_socket *socket, struct aws_channel_slot *slot, size_t max_read_size);
```
