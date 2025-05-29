```
aws_async_input_stream_init_base(stream, alloc, vtable, impl)
```

[`aws_async_input_stream`](@ref) "ベースクラス" を初期化します

### プロトタイプ

```c
void aws_async_input_stream_init_base( struct aws_async_input_stream *stream, struct aws_allocator *alloc, const struct aws_async_input_stream_vtable *vtable, void *impl);
```
