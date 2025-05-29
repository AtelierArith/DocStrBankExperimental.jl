Invoked when the data stream of an outgoing HTTP write operation is no longer in use. This is always invoked on the HTTP connection's event-loop thread.

# Arguments

  * `stream`: HTTP-stream this write operation was submitted to.
  * `error_code`: If error_code is AWS_ERROR_SUCCESS (0), the data was successfully sent. Any other error_code indicates that the HTTP-stream is in the process of terminating. If the error_code is AWS_ERROR_HTTP_STREAM_HAS_COMPLETED, the stream's termination has nothing to do with this write operation. Any other non-zero error code indicates a problem with this particular write operation's data.
  * `user_data`: User data for this write operation.
