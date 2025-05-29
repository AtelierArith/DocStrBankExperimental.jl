```
aws_channel_put_local_object(channel, key, obj)
```

Stores an object by key in the event loop's local storage.

### Prototype

```c
int aws_channel_put_local_object( struct aws_channel *channel, const void *key, const struct aws_event_loop_local_object *obj);
```
