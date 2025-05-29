```
aws_tls_connection_options_set_alpn_list(conn_options, allocator, alpn_list)
```

Sets alpn list in the form <protocol1;protocol2;...>. A maximum of 4 protocols are supported. alpn_list is copied. This value is already inherited from [`aws_tls_ctx`](@ref), but the [`aws_tls_ctx`](@ref) is expensive, and should be used across as many connections as possible. If you want to set this per connection, set it here.

### Prototype

```c
int aws_tls_connection_options_set_alpn_list( struct aws_tls_connection_options *conn_options, struct aws_allocator *allocator, const char *alpn_list);
```
