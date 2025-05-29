```
aws_input_stream_acquire(stream)
```

Increments the reference count on the input stream, allowing the caller to take a reference to it.

Returns the same input stream passed in.

### Prototype

```c
struct aws_input_stream *aws_input_stream_acquire(struct aws_input_stream *stream);
```
