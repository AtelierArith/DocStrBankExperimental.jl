```
aws_tls_connection_options_clean_up(connection_options)
```

Cleans up resources in [`aws_tls_connection_options`](@ref). This can be called immediately after initializing a tls handler, or if using the bootstrap api, immediately after asking for a channel.

### Prototype

```c
void aws_tls_connection_options_clean_up(struct aws_tls_connection_options *connection_options);
```
