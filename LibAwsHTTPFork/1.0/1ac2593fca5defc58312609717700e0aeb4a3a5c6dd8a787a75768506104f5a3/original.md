```
aws_http_headers_add(headers, name, value)
```

Add a header. The underlying strings are copied.

### Prototype

```c
int aws_http_headers_add(struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor value);
```
