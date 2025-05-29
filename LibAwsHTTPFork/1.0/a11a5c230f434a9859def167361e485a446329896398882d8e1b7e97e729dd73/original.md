```
aws_http_headers_erase_value(headers, name, value)
```

Remove the first header found with this name and value. AWS_ERROR_HTTP_HEADER_NOT_FOUND is raised if no such header is found.

### Prototype

```c
int aws_http_headers_erase_value( struct aws_http_headers *headers, struct aws_byte_cursor name, struct aws_byte_cursor value);
```
