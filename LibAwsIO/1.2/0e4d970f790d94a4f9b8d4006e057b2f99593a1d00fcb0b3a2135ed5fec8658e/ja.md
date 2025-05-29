```
aws_channel_remove_local_object(channel, key, removed_obj)
```

イベントループのローカルストレージからキーによってオブジェクトを削除します。

### プロトタイプ

```c
int aws_channel_remove_local_object( struct aws_channel *channel, const void *key, struct aws_event_loop_local_object *removed_obj);
```
