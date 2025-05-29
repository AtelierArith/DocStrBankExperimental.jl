```
aws_http_status_text(status_code)
```

Returns the description of common status codes. Ex: 404 -> "Not Found" An empty string is returned if the status code is not recognized.

### Prototype

```c
const char *aws_http_status_text(int status_code);
```
