```
aws_input_stream_release(stream)
```

Decrements a input stream's ref count. When the ref count drops to zero, the input stream will be destroyed.

Returns NULL always.

### Prototype

```c
struct aws_input_stream *aws_input_stream_release(struct aws_input_stream *stream);
```
