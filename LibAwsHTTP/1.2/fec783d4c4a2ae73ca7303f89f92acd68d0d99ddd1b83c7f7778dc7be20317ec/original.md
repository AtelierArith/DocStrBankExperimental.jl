```
aws_http_headers_get(headers, name, out_value)
```

Get the first value for this name, ignoring any additional values. AWS_ERROR_HTTP_HEADER_NOT_FOUND is raised if the name is not found.

### Prototype

```c
int aws_http_headers_get( const struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor *out_value);
```
