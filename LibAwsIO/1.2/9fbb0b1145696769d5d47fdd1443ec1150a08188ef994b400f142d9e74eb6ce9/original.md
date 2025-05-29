```
aws_pipe_clean_up_write_end(write_end)
```

Clean up the write-end of the pipe. This must be called on the thread of the connected event-loop.

### Prototype

```c
int aws_pipe_clean_up_write_end(struct aws_pipe_write_end *write_end);
```
