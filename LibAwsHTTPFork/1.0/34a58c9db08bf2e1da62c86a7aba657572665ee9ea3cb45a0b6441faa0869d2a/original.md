```
aws_http_headers_get_all(headers, name)
```

Get all values with this name, combined into one new aws_string that you are responsible for destroying. If there are multiple headers with this name, their values are appended with comma-separators. If there are no headers with this name, NULL is returned and AWS_ERROR_HTTP_HEADER_NOT_FOUND is raised.

### Prototype

```c
struct aws_string *aws_http_headers_get_all(const struct aws_http_headers *headers, struct aws_byte_cursor name);
```
