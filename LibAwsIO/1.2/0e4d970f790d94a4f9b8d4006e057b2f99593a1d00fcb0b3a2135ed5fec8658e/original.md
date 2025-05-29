```
aws_channel_remove_local_object(channel, key, removed_obj)
```

Removes an object by key from the event loop's local storage.

### Prototype

```c
int aws_channel_remove_local_object( struct aws_channel *channel, const void *key, struct aws_event_loop_local_object *removed_obj);
```
