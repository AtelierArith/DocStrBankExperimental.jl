```
aws_tls_client_handler_new(allocator, options, slot)
```

Creates a new tls channel handler in client mode. Options will be copied. You must call [`aws_tls_client_handler_start_negotiation`](@ref) and wait on the [`aws_tls_on_negotiation_result_fn`](@ref) callback before the handler can begin processing application data.

### Prototype

```c
struct aws_channel_handler *aws_tls_client_handler_new( struct aws_allocator *allocator, struct aws_tls_connection_options *options, struct aws_channel_slot *slot);
```
