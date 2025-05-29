Called in client mode when an outgoing connection has succeeded or an error has occurred. If the connection was successful error_code will be AWS_ERROR_SUCCESS and the socket has already been assigned to the event loop specified in [`aws_socket_connect`](@ref)().

If an error occurred error_code will be non-zero.
