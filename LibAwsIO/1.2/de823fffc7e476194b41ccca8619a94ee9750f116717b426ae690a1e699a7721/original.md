Called by a listening socket when either an incoming connection has been received or an error occurred.

In the normal use-case, this function will be called multiple times over the lifetime of a single listening socket. new_socket is already connected and initialized, and is using the same options and allocator as the listening socket. A user may want to call [`aws_socket_set_options`](@ref)() on the new socket if different options are desired.

new_socket is not yet assigned to an event-loop. The user should call [`aws_socket_assign_to_event_loop`](@ref)() before performing IO operations. The user must call `[`aws*socket*clean*up`](@ref)()` and "aws\*mem_release()" when they're done with the new_socket, to free it.

When error_code is AWS_ERROR_SUCCESS, new_socket is the recently accepted connection. If error_code is non-zero, an error occurred and you should [`aws_socket_close`](@ref)() the socket.

Do not call [`aws_socket_clean_up`](@ref)() from this callback.
