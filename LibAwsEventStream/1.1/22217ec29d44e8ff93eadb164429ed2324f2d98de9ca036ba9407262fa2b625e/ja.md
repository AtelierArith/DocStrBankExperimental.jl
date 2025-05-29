```
aws_event_stream_rpc_server_new_listener(allocator, options)
```

リスナーを参照カウント1で作成します。リスナーの使用が終了したら、[`aws_event_stream_rpc_server_listener_release`](@ref)()を呼び出す責任があります。エラーが発生した場合はNULLを返します。

### プロトタイプ

```c
struct aws_event_stream_rpc_server_listener *aws_event_stream_rpc_server_new_listener( struct aws_allocator *allocator, struct aws_event_stream_rpc_server_listener_options *options);
```
