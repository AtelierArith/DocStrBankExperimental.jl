```
aws_http2_headers_set_request_authority(h2_headers, authority)
```

Set `:authority` (request pseudo headers only). The pseudo headers makes its own copy of the underlying string.

### Prototype

```c
int aws_http2_headers_set_request_authority(struct aws_http_headers *h2_headers, struct aws_byte_cursor authority);
```
