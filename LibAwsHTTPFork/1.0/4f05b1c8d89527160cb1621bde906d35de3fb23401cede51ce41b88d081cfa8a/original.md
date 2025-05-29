```
aws_http_headers_add_array(headers, array, count)
```

Add an array of headers. The underlying strings are copied.

### Prototype

```c
int aws_http_headers_add_array(struct aws_http_headers *headers, const struct aws_http_header *array, size_t count);
```
