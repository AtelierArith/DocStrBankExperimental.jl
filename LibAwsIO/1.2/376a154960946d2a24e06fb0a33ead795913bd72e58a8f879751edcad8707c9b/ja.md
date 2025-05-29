```
aws_channel_put_local_object(channel, key, obj)
```

イベントループのローカルストレージにキーでオブジェクトを保存します。

### プロトタイプ

```c
int aws_channel_put_local_object( struct aws_channel *channel, const void *key, const struct aws_event_loop_local_object *obj);
```
