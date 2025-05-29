```
aws_http2_headers_get_response_status(h2_headers, out_status_code)
```

Get `:status` (response pseudo headers only). If no status is set, AWS_ERROR_HTTP_DATA_NOT_AVAILABLE is raised.

### Prototype

```c
int aws_http2_headers_get_response_status(const struct aws_http_headers *h2_headers, int *out_status_code);
```
