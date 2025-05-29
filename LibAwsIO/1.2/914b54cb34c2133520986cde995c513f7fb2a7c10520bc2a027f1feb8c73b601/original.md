Callback for when socket is either readable (edge-triggered) or when an error has occurred. If the socket is readable, error_code will be AWS_ERROR_SUCCESS.

`socket` may be NULL in the callback if the socket is released and cleaned up before the callback is triggered.
