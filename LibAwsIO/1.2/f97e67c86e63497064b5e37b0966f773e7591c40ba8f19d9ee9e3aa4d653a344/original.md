```
aws_pipe_get_write_end_event_loop(write_end)
```

Get the event-loop connected to the write-end of the pipe. This may be called on any thread.

### Prototype

```c
struct aws_event_loop *aws_pipe_get_write_end_event_loop(const struct aws_pipe_write_end *write_end);
```
