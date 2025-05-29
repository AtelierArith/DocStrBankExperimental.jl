Invoked when the data of an outgoing HTTP/1.1 chunk is no longer in use. This is always invoked on the HTTP connection's event-loop thread.

# Arguments

  * `stream`: HTTP-stream this chunk was submitted to.
  * `error_code`: If error_code is AWS_ERROR_SUCCESS (0), the data was successfully sent. Any other error_code indicates that the HTTP-stream is in the process of terminating. If the error_code is AWS_ERROR_HTTP_STREAM_HAS_COMPLETED, the stream's termination has nothing to do with this chunk. Any other non-zero error code indicates a problem with this particular chunk's data.
  * `user_data`: User data for this chunk.
