```
aws_http_headers_add_header(headers, header)
```

Add a header. The underlying strings are copied.

### Prototype

```c
int aws_http_headers_add_header(struct aws_http_headers *headers, const struct aws_http_header *header);
```
