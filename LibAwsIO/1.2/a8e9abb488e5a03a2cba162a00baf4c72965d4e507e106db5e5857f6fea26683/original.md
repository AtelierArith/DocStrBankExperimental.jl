```
aws_pipe_subscribe_to_readable_events(read_end, on_readable, user_data)
```

Subscribe to be notified when the pipe becomes readable (edge-triggered), or an error occurs. `on_readable` is invoked on the event-loop's thread when the pipe has data to read, or the pipe has an error. `on_readable` is invoked again any time the user reads all data, and then more data arrives. Note that it will not be invoked again if the pipe still has unread data when more data arrives. This must be called on the thread of the connected event-loop.

### Prototype

```c
int aws_pipe_subscribe_to_readable_events( struct aws_pipe_read_end *read_end, aws_pipe_on_readable_fn *on_readable, void *user_data);
```
