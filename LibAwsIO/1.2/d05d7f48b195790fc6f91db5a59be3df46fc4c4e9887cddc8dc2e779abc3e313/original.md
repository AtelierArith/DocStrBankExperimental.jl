Callback for when the data passed to a call to [`aws_socket_write`](@ref)() has either completed or failed. On success, error_code will be AWS_ERROR_SUCCESS.

`socket` may be NULL in the callback if the socket is released and cleaned up before the callback is triggered.
