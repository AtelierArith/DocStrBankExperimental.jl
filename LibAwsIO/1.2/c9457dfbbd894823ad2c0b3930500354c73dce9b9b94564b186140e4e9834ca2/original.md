```
aws_pipe_clean_up_read_end(read_end)
```

Clean up the read-end of the pipe. This must be called on the thread of the connected event-loop.

### Prototype

```c
int aws_pipe_clean_up_read_end(struct aws_pipe_read_end *read_end);
```
