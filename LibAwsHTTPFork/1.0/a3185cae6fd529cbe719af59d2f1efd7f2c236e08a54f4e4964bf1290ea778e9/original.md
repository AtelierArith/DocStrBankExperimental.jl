```
aws_http_stream_get_id(stream)
```

Gets the HTTP/2 id associated with a stream. Even h1 streams have an id (using the same allocation procedure as http/2) for easier tracking purposes. For client streams, this will only be non-zero after a successful call to [`aws_http_stream_activate`](@ref)()

### Prototype

```c
uint32_t aws_http_stream_get_id(const struct aws_http_stream *stream);
```
