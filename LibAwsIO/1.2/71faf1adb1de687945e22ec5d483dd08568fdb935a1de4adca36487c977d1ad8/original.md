```
aws_tls_handler_server_name(handler)
```

Client mode only. This is the server name that was used for SNI and host name validation.

### Prototype

```c
struct aws_byte_buf aws_tls_handler_server_name(struct aws_channel_handler *handler);
```
