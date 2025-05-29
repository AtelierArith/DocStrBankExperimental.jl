```
aws_http2_stream_manager_acquire_stream(http2_stream_manager, acquire_stream_option)
```

Acquire a stream from stream manager asynchronously.

# Arguments

  * `http2_stream_manager`:
  * `acquire_stream_option`: see [`aws_http2_stream_manager_acquire_stream_options`](@ref)

### Prototype

```c
void aws_http2_stream_manager_acquire_stream( struct aws_http2_stream_manager *http2_stream_manager, const struct aws_http2_stream_manager_acquire_stream_options *acquire_stream_option);
```
