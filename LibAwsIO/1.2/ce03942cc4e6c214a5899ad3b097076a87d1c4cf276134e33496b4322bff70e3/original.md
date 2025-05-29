```
aws_tls_server_handler_new(allocator, options, slot)
```

Creates a new tls channel handler in server mode. Options will be copied. You must wait on the [`aws_tls_on_negotiation_result_fn`](@ref) callback before the handler can begin processing application data.

### Prototype

```c
struct aws_channel_handler *aws_tls_server_handler_new( struct aws_allocator *allocator, struct aws_tls_connection_options *options, struct aws_channel_slot *slot);
```
