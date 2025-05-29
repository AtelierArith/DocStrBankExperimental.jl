```
aws_http_headers_erase_index(headers, index)
```

Remove the header at the specified index.

AWS_ERROR_INVALID_INDEX is raised if the index is invalid.

### Prototype

```c
int aws_http_headers_erase_index(struct aws_http_headers *headers, size_t index);
```
