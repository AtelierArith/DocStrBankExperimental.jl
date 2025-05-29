Invoked repeatedly times as headers are received. At this point, [`aws_http_stream_get_incoming_response_status`](@ref)() can be called for the client. And [`aws_http_stream_get_incoming_request_method`](@ref)() and [`aws_http_stream_get_incoming_request_uri`](@ref)() can be called for the server. This is always invoked on the HTTP connection's event-loop thread.

Return AWS_OP_SUCCESS to continue processing the stream. Return aws_raise_error(E) to indicate failure and cancel the stream. The error you raise will be reflected in the error_code passed to the on_complete callback.
