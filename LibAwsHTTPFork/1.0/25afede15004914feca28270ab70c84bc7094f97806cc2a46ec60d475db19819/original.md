```
aws_http_headers_erase(headers, name)
```

Remove all headers with this name. AWS_ERROR_HTTP_HEADER_NOT_FOUND is raised if no headers with this name are found.

### Prototype

```c
int aws_http_headers_erase(struct aws_http_headers *headers, struct aws_byte_cursor name);
```
