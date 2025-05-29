```
aws_async_input_stream_init_base(stream, alloc, vtable, impl)
```

Initialize [`aws_async_input_stream`](@ref) "base class"

### Prototype

```c
void aws_async_input_stream_init_base( struct aws_async_input_stream *stream, struct aws_allocator *alloc, const struct aws_async_input_stream_vtable *vtable, void *impl);
```
