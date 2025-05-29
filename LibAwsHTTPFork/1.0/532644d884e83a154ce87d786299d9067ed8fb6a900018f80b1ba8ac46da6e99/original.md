Invoked when connect completes.

If unsuccessful, error_code will be set, connection will be NULL, and the on_shutdown callback will never be invoked.

If successful, error_code will be 0 and connection will be valid. The user is now responsible for the connection and must call [`aws_http_connection_release`](@ref)() when they are done with it.

The connection uses one event-loop thread to do all its work. The thread invoking this callback will be the same thread that invokes all future callbacks for this connection and its streams.
