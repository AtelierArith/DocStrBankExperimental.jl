Invoked when the incoming header block of this type(informational/main/trailing) has been completely read. This is always invoked on the HTTP connection's event-loop thread.

Return AWS_OP_SUCCESS to continue processing the stream. Return aws_raise_error(E) to indicate failure and cancel the stream. The error you raise will be reflected in the error_code passed to the on_complete callback.
