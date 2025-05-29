```
testing_channel_set_downstream_handler_shutdown_callback(testing, on_shutdown, user_data)
```

Set a callback which is invoked during the handler's shutdown, once in the read direction and again in the write direction. Use this to inject actions that might occur in the middle of channel shutdown.

### Prototype

```c
static inline void testing_channel_set_downstream_handler_shutdown_callback( struct testing_channel *testing, testing_channel_handler_on_shutdown_fn *on_shutdown, void *user_data);
```
