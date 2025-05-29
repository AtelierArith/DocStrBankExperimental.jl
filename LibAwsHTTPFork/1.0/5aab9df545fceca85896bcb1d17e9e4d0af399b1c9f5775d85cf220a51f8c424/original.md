```
aws_http2_headers_get_request_method(h2_headers, out_method)
```

Get the `:method` value (HTTP/2 headers only).

### Prototype

```c
int aws_http2_headers_get_request_method(const struct aws_http_headers *h2_headers, struct aws_byte_cursor *out_method);
```
