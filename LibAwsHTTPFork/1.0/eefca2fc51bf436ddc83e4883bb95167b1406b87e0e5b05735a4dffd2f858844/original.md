```
aws_http1_stream_add_chunked_trailer(http1_stream, trailing_headers)
```

Add a list of headers to be added as trailing headers sent after the last chunk is sent. a "Trailer" header field which indicates the fields present in the trailer.

Certain headers are forbidden in the trailer (e.g., Transfer-Encoding, Content-Length, Host). See RFC-7541 Section 4.1.2 for more details.

For client streams, activate() must be called before any chunks are submitted.

For server streams, the response must be submitted before the trailer can be added

[`aws_http1_stream_add_chunked_trailer`](@ref) must be called before the final size 0 chunk, and at the moment can only be called once, though this could change if need be.

Returns AWS_OP_SUCCESS if the chunk has been submitted.

### Prototype

```c
int aws_http1_stream_add_chunked_trailer( struct aws_http_stream *http1_stream, const struct aws_http_headers *trailing_headers);
```
