```
aws_tls_server_ctx_new(alloc, options)
```

Creates a new server ctx. This ctx can be used for the lifetime of the application assuming you want the same options for every incoming connection. Options will be copied.

### Prototype

```c
struct aws_tls_ctx *aws_tls_server_ctx_new( struct aws_allocator *alloc, const struct aws_tls_ctx_options *options);
```
