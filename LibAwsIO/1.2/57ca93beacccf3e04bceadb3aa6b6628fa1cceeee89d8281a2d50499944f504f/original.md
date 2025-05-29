Called by a listening socket when a listener accept has successfully initialized or an error has occurred. If the listener was successful error_code will be AWS_ERROR_SUCCESS and the socket has already been assigned to the event loop specified in [`aws_socket_start_accept`](@ref)().

If an error occurred error_code will be non-zero.
