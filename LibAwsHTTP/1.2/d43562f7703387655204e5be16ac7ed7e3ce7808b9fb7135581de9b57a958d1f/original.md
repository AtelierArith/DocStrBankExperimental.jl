```
aws_http2_headers_set_request_method(h2_headers, method)
```

Set `:method` (HTTP/2 headers only). The headers makes its own copy of the underlying string.

### Prototype

```c
int aws_http2_headers_set_request_method(struct aws_http_headers *h2_headers, struct aws_byte_cursor method);
```
