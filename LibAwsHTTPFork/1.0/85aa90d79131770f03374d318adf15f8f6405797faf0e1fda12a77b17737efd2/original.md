```
aws_http_headers_new(allocator)
```

Create a new headers object. The caller has a hold on the object and must call [`aws_http_headers_release`](@ref)() when they are done with it.

### Prototype

```c
struct aws_http_headers *aws_http_headers_new(struct aws_allocator *allocator);
```
