```
aws_pipe_write(write_end, src_buffer, on_completed, user_data)
```

Initiates an asynchrous write from the source buffer to the pipe. The data referenced by `src_buffer` must remain in memory until the operation completes. `on_complete` is called on the event-loop thread when the operation has either completed or failed. The callback's pipe argument will be NULL if the callback is invoked after the pipe has been cleaned up. This must be called on the thread of the connected event-loop.

### Prototype

```c
int aws_pipe_write( struct aws_pipe_write_end *write_end, struct aws_byte_cursor src_buffer, aws_pipe_on_write_completed_fn *on_completed, void *user_data);
```
