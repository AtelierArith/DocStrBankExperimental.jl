```
aws_http_headers_acquire(headers)
```

Acquire a hold on the object, preventing it from being deleted until [`aws_http_headers_release`](@ref)() is called by all those with a hold on it.

### Prototype

```c
void aws_http_headers_acquire(struct aws_http_headers *headers);
```
