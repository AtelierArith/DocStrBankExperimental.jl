```
aws_tls_connection_options_set_callbacks(conn_options, on_negotiation_result, on_data_read, on_error, user_data)
```

Sets callbacks for use with a tls connection.

### Prototype

```c
void aws_tls_connection_options_set_callbacks( struct aws_tls_connection_options *conn_options, aws_tls_on_negotiation_result_fn *on_negotiation_result, aws_tls_on_data_read_fn *on_data_read, aws_tls_on_error_fn *on_error, void *user_data);
```
