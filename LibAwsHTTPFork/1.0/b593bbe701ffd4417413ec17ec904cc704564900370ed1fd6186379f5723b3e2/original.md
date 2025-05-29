Called repeatedly as body data is received. The data must be copied immediately if you wish to preserve it. This is always invoked on the HTTP connection's event-loop thread.

Note that, if the connection is using manual_window_management then the window size has shrunk by the amount of body data received. If the window size reaches 0 no further data will be received. Increment the window size with [`aws_http_stream_update_window`](@ref)().

Return AWS_OP_SUCCESS to continue processing the stream. Return aws_raise_error(E) to indicate failure and cancel the stream. The error you raise will be reflected in the error_code passed to the on_complete callback.
