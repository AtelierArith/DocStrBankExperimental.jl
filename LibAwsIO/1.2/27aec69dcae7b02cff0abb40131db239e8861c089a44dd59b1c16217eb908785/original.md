```
aws_pipe_get_read_end_event_loop(read_end)
```

Get the event-loop connected to the read-end of the pipe. This may be called on any thread.

### Prototype

```c
struct aws_event_loop *aws_pipe_get_read_end_event_loop(const struct aws_pipe_read_end *read_end);
```
