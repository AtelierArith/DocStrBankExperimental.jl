```
aws_tls_client_ctx_new(alloc, options)
```

Creates a new client ctx. This ctx can be used for the lifetime of the application assuming you want the same options for every outgoing connection. Options will be copied.

### Prototype

```c
struct aws_tls_ctx *aws_tls_client_ctx_new( struct aws_allocator *alloc, const struct aws_tls_ctx_options *options);
```
