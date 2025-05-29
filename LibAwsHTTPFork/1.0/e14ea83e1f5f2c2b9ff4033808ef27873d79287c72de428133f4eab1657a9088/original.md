```
aws_http2_stream_write_data(http2_stream, options)
```

The stream must have specified `http2_use_manual_data_writes` during request creation. For client streams, activate() must be called before any frames are submitted. For server streams, the response headers must be submitted before any frames. A write with options that has end_stream set to be true will end the stream and prevent any further write.

Typical usage will be something like: options.http2_use_manual_data_writes = true; stream = [`aws_http_connection_make_request`](@ref)(connection, &options); [`aws_http_stream_activate`](@ref)(stream); ... struct [`aws_http2_stream_write_data_options`](@ref) write; [`aws_http2_stream_write_data`](@ref)(stream, &write); ... struct [`aws_http2_stream_write_data_options`](@ref) last_write; last_write.end_stream = true; [`aws_http2_stream_write_data`](@ref)(stream, &write); ... [`aws_http_stream_release`](@ref)(stream);

# Returns

AWS_OP_SUCCESS if the write was queued AWS_OP_ERROR indicating the attempt raised an error code. AWS_ERROR_INVALID_STATE will be raised for invalid usage. AWS_ERROR_HTTP_STREAM_HAS_COMPLETED will be raised if the stream ended for reasons behind the scenes.

### Prototype

```c
int aws_http2_stream_write_data( struct aws_http_stream *http2_stream, const struct aws_http2_stream_write_data_options *options);
```
