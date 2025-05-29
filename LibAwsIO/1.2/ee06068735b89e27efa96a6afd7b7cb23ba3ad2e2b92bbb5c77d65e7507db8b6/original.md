```
aws_tls_connection_options_set_server_name(conn_options, allocator, server_name)
```

Sets server name to use for the SNI extension (supported everywhere), as well as x.509 validation. If you don't set this, your x.509 validation will likely fail.

### Prototype

```c
int aws_tls_connection_options_set_server_name( struct aws_tls_connection_options *conn_options, struct aws_allocator *allocator, const struct aws_byte_cursor *server_name);
```
