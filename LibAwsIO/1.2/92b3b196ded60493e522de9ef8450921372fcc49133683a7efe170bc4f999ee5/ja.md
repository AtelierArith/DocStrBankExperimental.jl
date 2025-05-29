```
aws_channel_fetch_local_object(channel, key, obj)
```

イベントループのローカルストレージからキーによってオブジェクトを取得します。

### プロトタイプ

```c
int aws_channel_fetch_local_object( struct aws_channel *channel, const void *key, struct aws_event_loop_local_object *obj);
```
