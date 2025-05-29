```
aws_pipe_init(read_end, read_end_event_loop, write_end, write_end_event_loop, allocator)
```

Opens an OS specific bidirectional pipe. The read direction is stored in read_end. Write direction is stored in write_end. Each end must be connected to an event-loop, and further calls to each end must happen on that event-loop's thread.

### Prototype

```c
int aws_pipe_init( struct aws_pipe_read_end *read_end, struct aws_event_loop *read_end_event_loop, struct aws_pipe_write_end *write_end, struct aws_event_loop *write_end_event_loop, struct aws_allocator *allocator);
```
