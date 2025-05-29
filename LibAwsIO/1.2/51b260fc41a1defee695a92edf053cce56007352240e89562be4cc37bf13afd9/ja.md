```
aws_server_bootstrap_new(allocator, el_group)
```

`allocator` と `el_group` でサーバーブートストラップを初期化します。このオブジェクトはリスナー、サーバー接続、およびチャネルを管理します。

### プロトタイプ

```c
struct aws_server_bootstrap *aws_server_bootstrap_new( struct aws_allocator *allocator, struct aws_event_loop_group *el_group);
```
