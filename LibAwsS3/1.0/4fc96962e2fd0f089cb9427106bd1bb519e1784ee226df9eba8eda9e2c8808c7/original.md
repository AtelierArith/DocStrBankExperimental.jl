```
aws_s3_meta_request_write(meta_request, data, eof)
```

Write the next chunk of data.

You must set `[`aws*s3*meta*request*options`](@ref).send\_using\_async\_writes` to use this function.

This function is asynchronous, and returns a future (see <aws/io/future.h>). You may not call write() again until the future completes.

If the future completes with an error code, then write() did not succeed and you should not call it again. If the future contains any error code, the meta request is guaranteed to finish soon (you don't need to worry about canceling the meta request yourself after a failed write). A common error code is AWS_ERROR_S3_REQUEST_HAS_COMPLETED, indicating the meta request completed for reasons unrelated to the write() call (e.g. CreateMultipartUpload received a 403 Forbidden response). AWS_ERROR_INVALID_STATE usually indicates that you're calling write() incorrectly (e.g. not waiting for previous write to complete).

You MUST keep the data in memory until the future completes. If you need to free the memory early, call [`aws_s3_meta_request_cancel`](@ref)(). cancel() will synchronously complete the future from any pending write with error code AWS_ERROR_S3_REQUEST_HAS_COMPLETED.

You can wait any length of time between calls to write(). If there's not enough data to upload a part, the data will be copied to a buffer and the future will immediately complete.

This function never returns NULL.

WARNING: This feature is experimental.

# Arguments

  * `meta_request`: Meta request
  * `data`: The data to send. The data can be any size.
  * `eof`: Pass true to signal EOF (end of file). Do not call write() again after passing true.

### Prototype

```c
struct aws_future_void *aws_s3_meta_request_write( struct aws_s3_meta_request *meta_request, struct aws_byte_cursor data, bool eof);
```
