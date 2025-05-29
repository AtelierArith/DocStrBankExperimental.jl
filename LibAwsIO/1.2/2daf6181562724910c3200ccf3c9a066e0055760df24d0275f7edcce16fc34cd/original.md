```
aws_pipe_unsubscribe_from_readable_events(read_end)
```

Stop receiving notifications about events on the read-end of the pipe. This must be called on the thread of the connected event-loop.

### Prototype

```c
int aws_pipe_unsubscribe_from_readable_events(struct aws_pipe_read_end *read_end);
```
