Invoked when a new connection is received on a server listener. If you return AWS_OP_SUCCESS, You must fill in the fields for connection_options or the program will assert and exit.

If error_code is non-zero, an error occurred upon setting up the channel and connection will be NULL. Otherwise, connection is non-null. If you intend to seat a pointer to connection, you MUST call [`aws_event_stream_rpc_server_connection_acquire`](@ref)() and when you're finished with the connection you MUST call aws_event_stream_server_connection_release().
