```
aws_http_headers_has(headers, name)
```

Test if header name exists or not in headers

### Prototype

```c
bool aws_http_headers_has(const struct aws_http_headers *headers, struct aws_byte_cursor name);
```
