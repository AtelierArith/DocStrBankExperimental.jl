```
aws_http_headers_release(headers)
```

Release a hold on the object. The object is deleted when all holds on it are released.

### Prototype

```c
void aws_http_headers_release(struct aws_http_headers *headers);
```
