```
aws_http_server_release(server)
```

Release the server. It will close the listening socket and all the connections existing in the server. The on_destroy_complete will be invoked when the destroy operation completes

### Prototype

```c
void aws_http_server_release(struct aws_http_server *server);
```
