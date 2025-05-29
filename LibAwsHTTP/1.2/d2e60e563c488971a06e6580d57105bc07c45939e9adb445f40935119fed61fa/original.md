```
aws_http1_stream_write_chunk(http1_stream, options)
```

Submit a chunk of data to be sent on an HTTP/1.1 stream. The stream must have specified "chunked" in a "transfer-encoding" header, and the [`aws_http_message`](@ref) must NOT have any body stream set. For client streams, activate() must be called before any chunks are submitted. For server streams, the response must be submitted before any chunks. A final chunk with size 0 must be submitted to successfully complete the HTTP-stream.

Returns AWS_OP_SUCCESS if the chunk has been submitted. The chunk's completion callback will be invoked when the HTTP-stream is done with the chunk data, whether or not it was successfully sent (see [`aws_http1_stream_write_chunk_complete_fn`](@ref)). The chunk data must remain valid until the completion callback is invoked.

Returns AWS_OP_ERR and raises an error if the chunk could not be submitted. In this case, the chunk's completion callback will never be invoked. Note that it is always possible for the HTTP-stream to terminate unexpectedly prior to this call being made, in which case the error raised is AWS_ERROR_HTTP_STREAM_HAS_COMPLETED.

### Prototype

```c
int aws_http1_stream_write_chunk( struct aws_http_stream *http1_stream, const struct aws_http1_chunk_options *options);
```
