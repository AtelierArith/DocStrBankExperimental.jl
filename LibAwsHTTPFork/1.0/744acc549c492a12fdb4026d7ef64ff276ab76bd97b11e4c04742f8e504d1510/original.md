```
aws_http_headers_set(headers, name, value)
```

Set a header value. The header is added if necessary and any existing values for this name are removed. The underlying strings are copied.

### Prototype

```c
int aws_http_headers_set(struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor value);
```
