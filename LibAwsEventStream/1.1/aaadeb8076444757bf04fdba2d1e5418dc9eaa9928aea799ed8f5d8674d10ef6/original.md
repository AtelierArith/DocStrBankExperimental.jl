Invoked when a connection attempt completes.

If the attempt was unsuccessful, the error_code will be non-zero and the connection pointer will be NULL, and [`aws_event_stream_rpc_client_on_connection_shutdown_fn`](@ref) will not be invoked.

If the attempt was successful, error_code will be 0 and the connection pointer will be valid. You must call [`aws_event_stream_rpc_client_connection_acquire`](@ref)() to prevent the pointer's memory from being destroyed before you are ready. When you are completely done with the connection pointer you must call [`aws_event_stream_rpc_client_connection_release`](@ref)() or its memory will leak. [`aws_event_stream_rpc_client_on_connection_shutdown_fn`](@ref) will be invoked when the network connection has closed. If you are done with the connection, but it is still open, you must call aws_aws_event_stream_rpc_client_close() or network connection will remain open, even if you call release().
