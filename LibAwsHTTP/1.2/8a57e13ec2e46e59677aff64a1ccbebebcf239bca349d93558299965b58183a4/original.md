```
aws_http2_headers_set_response_status(h2_headers, status_code)
```

Set `:status` (response pseudo headers only).

### Prototype

```c
int aws_http2_headers_set_response_status(struct aws_http_headers *h2_headers, int status_code);
```
