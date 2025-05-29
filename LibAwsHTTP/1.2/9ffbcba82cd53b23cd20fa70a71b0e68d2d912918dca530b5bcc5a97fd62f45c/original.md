```
aws_http2_headers_set_request_path(h2_headers, path)
```

Set `:path` (request pseudo headers only). The pseudo headers makes its own copy of the underlying string.

### Prototype

```c
int aws_http2_headers_set_request_path(struct aws_http_headers *h2_headers, struct aws_byte_cursor path);
```
