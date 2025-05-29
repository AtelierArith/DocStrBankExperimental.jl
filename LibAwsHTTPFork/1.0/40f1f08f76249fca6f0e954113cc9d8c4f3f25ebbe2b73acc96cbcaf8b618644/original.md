```
aws_http_client_connect(options)
```

Asynchronously establish a client connection. The on_setup callback is invoked when the operation has created a connection or failed.

### Prototype

```c
int aws_http_client_connect(const struct aws_http_client_connection_options *options);
```
