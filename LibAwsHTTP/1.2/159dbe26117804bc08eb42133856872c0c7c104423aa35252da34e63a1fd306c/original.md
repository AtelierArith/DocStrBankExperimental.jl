Invoked when the data of an outgoing HTTP2 data frame is no longer in use. This is always invoked on the HTTP connection's event-loop thread.

# Arguments

  * `stream`: HTTP2-stream this write was submitted to.
  * `error_code`: If error_code is AWS_ERROR_SUCCESS (0), the data was successfully sent. Any other error_code indicates that the HTTP-stream is in the process of terminating. If the error_code is AWS_ERROR_HTTP_STREAM_HAS_COMPLETED, the stream's termination has nothing to do with this write. Any other non-zero error code indicates a problem with this particular write's data.
  * `user_data`: User data for this write.
