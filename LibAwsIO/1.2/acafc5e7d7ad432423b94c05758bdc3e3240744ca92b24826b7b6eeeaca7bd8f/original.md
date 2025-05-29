If TLS is being used, this function is called once the socket has received an incoming connection, the channel has been initialized, and TLS has been successfully negotiated. A TLS handler has already been added to the channel. If TLS negotiation fails, this function will be called with the corresponding error code.

If TLS is not being used, this function is called once the socket has received an incoming connection and the channel has been initialized.

This function is always called within the thread of the event-loop that the new channel is assigned to upon success.

On failure, the channel might not be assigned to an event loop yet, and will thus be invoked on the listener's event-loop thread.

This function does NOT mean "success", if error_code is AWS_OP_SUCCESS then everything was successful, otherwise an error condition occurred.

If an error occurred, you do not need to shutdown the channel. The `aws_channel_client_shutdown_callback` will be invoked once the channel has finished shutting down.
