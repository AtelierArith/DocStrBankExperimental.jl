```
aws_tls_connection_options_init_from_ctx(conn_options, ctx)
```

Initializes default connection options from an instance ot [`aws_tls_ctx`](@ref).

### Prototype

```c
void aws_tls_connection_options_init_from_ctx( struct aws_tls_connection_options *conn_options, struct aws_tls_ctx *ctx);
```
