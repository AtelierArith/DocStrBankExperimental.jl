```
aws_http2_headers_set_request_scheme(h2_headers, scheme)
```

Set `:scheme` (request pseudo headers only). The pseudo headers makes its own copy of the underlying string.

### Prototype

```c
int aws_http2_headers_set_request_scheme(struct aws_http_headers *h2_headers, struct aws_byte_cursor scheme);
```
