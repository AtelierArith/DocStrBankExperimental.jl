```
aws_tls_alpn_handler_new(allocator, on_protocol_negotiated, user_data)
```

Creates a channel handler, for client or server mode, that handles alpn. This isn't necessarily required since you can always call [`aws_tls_handler_protocol`](@ref) in the [`aws_tls_on_negotiation_result_fn`](@ref) callback, but this makes channel bootstrap easier to handle.

### Prototype

```c
struct aws_channel_handler *aws_tls_alpn_handler_new( struct aws_allocator *allocator, aws_tls_on_protocol_negotiated on_protocol_negotiated, void *user_data);
```
