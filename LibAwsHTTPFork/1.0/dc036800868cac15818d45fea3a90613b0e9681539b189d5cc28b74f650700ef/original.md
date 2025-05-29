```
aws_http_connection_stop_new_requests(connection)
```

Stop accepting new requests for the connection. It will NOT start the shutdown process for the connection. The requests that are already open can still wait to be completed, but new requests will fail to be created,

### Prototype

```c
void aws_http_connection_stop_new_requests(struct aws_http_connection *connection);
```
